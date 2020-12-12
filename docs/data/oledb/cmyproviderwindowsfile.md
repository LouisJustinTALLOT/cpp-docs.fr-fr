---
description: 'En savoir plus sur : CCustomWindowsFile'
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: c0df2840b68a350f9d65102fdf0a962681edefd9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170397"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

L’Assistant crée une classe qui contient une ligne de données ; dans ce cas, il est appelé `CCustomWindowsFile` . Le code suivant pour `CCustomWindowsFile` est généré par l’Assistant et répertorie tous les fichiers d’un répertoire à l’aide de la `WIN32_FIND_DATA` structure. `CCustomWindowsFile` hérite de la `WIN32_FIND_DATA` structure :

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

`CCustomWindowsFile` est appelé la [classe d’enregistrement utilisateur](../../data/oledb/user-record.md) , car elle comporte également un mappage décrivant les colonnes de l’ensemble de lignes du fournisseur. Le mappage de colonnes du fournisseur contient une entrée pour chaque champ de l’ensemble de lignes à l’aide des macros de PROVIDER_COLUMN_ENTRY. Les macros spécifient le nom de colonne, l’ordinal et le décalage d’une entrée de structure. Les entrées de colonne du fournisseur dans le code ci-dessus contiennent des décalages dans la `WIN32_FIND_DATA` structure. Lorsque le consommateur appelle `IRowset::GetData` , les données sont transférées dans une mémoire tampon contiguë. Au lieu d’effectuer des opérations arithmétiques sur les pointeurs, la carte vous permet de spécifier un membre de données.

La `CCustomRowset` classe contient également la `Execute` méthode. `Execute` est ce qui lit réellement les données dans à partir de la source native. Le code suivant illustre la méthode générée par l’Assistant `Execute` . La fonction utilise les `FindFirstFile` API Win32 et `FindNextFile` pour récupérer des informations sur les fichiers dans le répertoire et les placer dans des instances de la `CCustomWindowsFile` classe.

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

Le répertoire dans lequel effectuer la recherche s’affiche `m_strCommandText` ; il contient le texte représenté par l' `ICommandText` interface dans l’objet Command. Si aucun répertoire n’est spécifié, le répertoire actif est utilisé.

La méthode crée une entrée pour chaque fichier (correspondant à une ligne) et la place dans le `m_rgRowData` membre de données. La `CRowsetImpl` classe définit le `m_rgRowData` membre de données. Les données de ce tableau affichent la table entière et sont utilisées dans les modèles.

## <a name="see-also"></a>Voir aussi

[Fichiers de Wizard-Generated du fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
