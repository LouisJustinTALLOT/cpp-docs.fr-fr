---
title: Stockage de chaînes dans le fournisseur OLE DB
ms.date: 10/26/2018
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 5dce7dac84ef69da17baac135a68bd78698c4456
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026407"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Stockage de chaînes dans le fournisseur OLE DB

Dans *personnalisé*RS.h, le **Assistant fournisseur OLE DB ATL** crée un enregistrement d’utilisateur par défaut appelé `CWindowsFile`. Pour gérer les deux chaînes, modifier `CWindowsFile` comme indiqué dans le code suivant :

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

Les membres de données `szCommand` et `szText` représentent les deux chaînes, avec `szCommand2` et `szText2` avec des colonnes supplémentaires si nécessaire. Le membre de données `dwBookmark` n’est pas nécessaire pour ce fournisseur simple en lecture seule, mais sera utilisé ultérieurement pour ajouter un `IRowsetLocate` interface ; consultez [amélioration de la Simple lecture seul fournisseur](../../data/oledb/enhancing-the-simple-read-only-provider.md). Le `==` opérateur compare des instances (l’implémentation de cet opérateur est facultatif).

Dans ce cas, vous pouvez ajouter les fonctionnalités de [lecture de chaînes dans le fournisseur OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

## <a name="see-also"></a>Voir aussi

[Implémentation d'un fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
