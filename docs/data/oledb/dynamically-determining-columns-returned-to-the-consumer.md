---
description: 'En savoir plus sur : détermination dynamique des colonnes retournées au consommateur'
title: Détermination de manière dynamique des colonnes retournées au consommateur
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: fd70164edff5b9267e01a891a143920ac4e60a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287565"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Détermination de manière dynamique des colonnes retournées au consommateur

Les macros PROVIDER_COLUMN_ENTRY gèrent normalement l' `IColumnsInfo::GetColumnsInfo` appel. Toutefois, étant donné qu’un consommateur peut choisir d’utiliser des signets, le fournisseur doit être en mesure de modifier les colonnes retournées selon que le consommateur demande ou non un signet.

Pour gérer l' `IColumnsInfo::GetColumnsInfo` appel, supprimez le PROVIDER_COLUMN_MAP, qui définit une fonction `GetColumnInfo` , à partir de l' `CCustomWindowsFile` enregistrement utilisateur dans RS. h *personnalisé* et remplacez-le par la définition de votre propre `GetColumnInfo` fonction :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CCustomWindowsFile
{
public:
   DWORD dwBookmark;
   static const int iSize = 256;
   TCHAR szCommand[iSize];
   TCHAR szText[iSize];
   TCHAR szCommand2[iSize];
   TCHAR szText2[iSize];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CCustomWindowsFile& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

Ensuite, implémentez la `GetColumnInfo` fonction dans *personnalisé* RS. cpp, comme indiqué dans le code suivant.

`GetColumnInfo` vérifie d’abord si la propriété OLE DB `DBPROP_BOOKMARKS` est définie. Pour obtenir la propriété, `GetColumnInfo` utilise un pointeur ( `pRowset` ) vers l’objet d’ensemble de lignes. Le `pThis` pointeur représente la classe qui a créé l’ensemble de lignes, qui est la classe où le mappage de propriété est stocké. `GetColumnInfo` conversions `pThis` pointeur vers un `RCustomRowset` pointeur.

Pour vérifier la `DBPROP_BOOKMARKS` propriété, `GetColumnInfo` utilise l' `IRowsetInfo` interface, que vous pouvez obtenir en appelant `QueryInterface` sur l' `pRowset` interface. Vous pouvez également utiliser une méthode ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) à la place.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CCustomWindowsFile::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero
   // ordinal entry in the column map with the bookmark information.
   CCustomRowset* pRowset = (CCustomRowset*) pThis;
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;
  
   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;
  
   if (spRowsetProps)
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);
  
   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
         DBTYPE_BYTES, 0, 0, GUID_NULL, CCustomWindowsFile, dwBookmark,
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CCustomWindowsFile, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

Cet exemple utilise un tableau statique pour contenir les informations de colonne. Si le consommateur ne souhaite pas la colonne de signets, une entrée dans le tableau n’est pas utilisée. Pour gérer les informations, vous créez deux macros de tableau : ADD_COLUMN_ENTRY et ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX prend un paramètre supplémentaire, *Flags*, qui est nécessaire si vous désignez une colonne de signets.

```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = flags; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \  
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \  
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;  
```

Dans la `GetColumnInfo` fonction, la macro Bookmark est utilisée comme suit :

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Vous pouvez maintenant compiler et exécuter le fournisseur amélioré. Pour tester le fournisseur, modifiez le consommateur de test comme décrit dans [implémentation d’un consommateur simple](../../data/oledb/implementing-a-simple-consumer.md). Exécutez le consommateur de test avec le fournisseur et vérifiez que le consommateur de test récupère les chaînes appropriées auprès du fournisseur.

## <a name="see-also"></a>Voir aussi

[Amélioration du fournisseur de Read-Only simple](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
