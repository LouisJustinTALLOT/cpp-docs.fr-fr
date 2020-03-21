---
title: Stockage de chaînes dans le fournisseur OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 1d6d2b73495d5ca6e275b13ed3c430f8169179d4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079107"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Stockage de chaînes dans le fournisseur OLE DB

> [!NOTE]
> L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures.

Dans *Custom*RS.h, l’**Assistant Fournisseur OLE DB ATL** crée un enregistrement utilisateur par défaut appelé `CWindowsFile`. Pour gérer les deux chaînes, modifiez `CWindowsFile` comme montré dans le code suivant :

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

Les membres de données `szCommand` et `szText` représentent les deux chaînes, avec `szCommand2` et `szText2` avec des colonnes supplémentaires en cas de besoin. Le membre de données `dwBookmark` n’est pas nécessaire pour ce fournisseur en lecture simple, mais est utilisé ultérieurement pour ajouter une interface `IRowsetLocate`. Consultez [Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md). L’opérateur `==` compare des instances (l’implémentation de cet opérateur est facultative).

Une fois fait, vous pouvez ajouter la fonctionnalité de [Lecture de chaînes dans le fournisseur OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

## <a name="see-also"></a>Voir aussi

[Implémentation d’un fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
