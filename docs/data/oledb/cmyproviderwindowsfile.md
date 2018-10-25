---
title: CCustomWindowsFile | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 947efa181a6b632050c01c4f2b327cf11a113e3f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070931"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

L’Assistant crée une classe pour contenir une ligne de données ; Dans ce cas, elle est appelée `CCustomWindowsFile`. Le code suivant pour `CCustomWindowsFile` est généré par un Assistant et répertorie tous les fichiers dans un répertoire à l’aide de la `WIN32_FIND_DATA` structure. `CCustomWindowsFile` hérite le `WIN32_FIND_DATA` structure :

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` est appelé le [classe d’enregistrement utilisateur](../../data/oledb/user-record.md) , car elle contient également un mappage décrivant les colonnes dans l’ensemble de lignes du fournisseur. Le mappage de colonnes du fournisseur contient une entrée pour chaque champ dans l’ensemble de lignes que l’utilisation des macros PROVIDER_COLUMN_ENTRY. Les macros spécifient le nom de colonne ordinal et l’offset pour une entrée de la structure. Dans le code ci-dessus, les entrées de colonne du fournisseur contiennent des offsets dans la `WIN32_FIND_DATA` structure. Lorsque le consommateur appelle `IRowset::GetData`, données sont transférées dans une mémoire tampon contiguë. Plutôt que d’effectuer d’effectuer l’opération arithmétique de pointeur, le mappage vous permet de spécifier un membre de données.

Le `CCustomRowset` classe contient également le `Execute` (méthode). `Execute` est ce qui lit les données dans la source native. Le code suivant montre le générées par l’Assistant `Execute` (méthode). La fonction utilise Win32 `FindFirstFile` et `FindNextFile` API pour récupérer des informations sur les fichiers dans le répertoire et les placer dans des instances de la `CCustomWindowsFile` classe.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

Le répertoire à Explorer est représenté par `m_strCommandText`; il contient le texte représenté par le `ICommandText` interface dans l’objet de commande. Si aucun répertoire n’est spécifié, il utilise le répertoire actif.

La méthode crée une entrée pour chaque fichier (correspondant à une ligne) et le place dans le `m_rgRowData` membre de données. Le `CRowsetImpl` classe définit la `m_rgRowData` membre de données. Les données de ce tableau représentent la table entière et sont utilisées dans tous les modèles.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)