---
description: 'En savoir plus sur : prise en charge des signets par le fournisseur'
title: Prise en charge des signets par le fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 0a2225f44d9d094f52e97b88eb58c6942906edf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286655"
---
# <a name="provider-support-for-bookmarks"></a>Prise en charge des signets par le fournisseur

L’exemple de cette rubrique ajoute l' `IRowsetLocate` interface à la `CCustomRowset` classe. Dans presque tous les cas, vous commencez par ajouter une interface à un objet COM existant. Vous pouvez ensuite la tester en ajoutant des appels à partir des modèles du consommateur. L’exemple montre comment :

- Ajoutez une interface à un fournisseur.

- Déterminez dynamiquement les colonnes à retourner au consommateur.

- Ajoutez la prise en charge des signets.

L'interface `IRowsetLocate` hérite de l'interface `IRowset` . Pour ajouter l' `IRowsetLocate` interface, héritez `CCustomRowset` de [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).

L’ajout de l' `IRowsetLocate` interface est un peu différent de la plupart des interfaces. Pour que les vtable soient alignées, les modèles de fournisseur OLE DB ont un paramètre de modèle pour gérer l’interface dérivée. Le code suivant montre la nouvelle liste d’héritage :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Les quatrième, cinquième et sixième paramètres sont ajoutés. Cet exemple utilise les valeurs par défaut pour les quatrième et cinquième paramètres, mais spécifie `IRowsetLocateImpl` comme sixième paramètre. `IRowsetLocateImpl` est une classe de modèle OLE DB qui accepte deux paramètres de modèle : ils raccordent l' `IRowsetLocate` interface à la `CCustomRowset` classe. Pour ajouter la plupart des interfaces, vous pouvez ignorer cette étape et passer à la suivante. Seules les `IRowsetLocate` `IRowsetScroll` interfaces et doivent être gérées de cette manière.

Vous devez ensuite indiquer au `CCustomRowset` à appeler `QueryInterface` pour l' `IRowsetLocate` interface. Ajoutez la ligne `COM_INTERFACE_ENTRY(IRowsetLocate)` à la carte. Le mappage d’interface pour `CCustomRowset` doit apparaître comme indiqué dans le code suivant :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Vous devez également raccorder votre mappage à la `CRowsetImpl` classe. Ajoutez dans la macro COM_INTERFACE_ENTRY_CHAIN pour effectuer un raccordement dans le `CRowsetImpl` mappage. Créez également un typedef appelé `RowsetBaseClass` qui se compose des informations d’héritage. Ce typedef est arbitraire et peut être ignoré.

Enfin, gérez l' `IColumnsInfo::GetColumnsInfo` appel. Pour ce faire, vous devez normalement utiliser les macros PROVIDER_COLUMN_ENTRY. Toutefois, un consommateur peut vouloir utiliser des signets. Vous devez être en mesure de modifier les colonnes retournées par le fournisseur selon que le consommateur demande un signet ou non.

Pour gérer l' `IColumnsInfo::GetColumnsInfo` appel, supprimez le mappage de PROVIDER_COLUMN dans la `CTextData` classe. La macro PROVIDER_COLUMN_MAP définit une fonction `GetColumnInfo` . Définissez votre propre `GetColumnInfo` fonction. La déclaration de fonction doit ressembler à ceci :

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

Ensuite, implémentez la `GetColumnInfo` fonction dans le fichier RS. cpp *personnalisé* comme suit :

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo` vérifie d’abord si une propriété appelée `DBPROP_IRowsetLocate` est définie. OLE DB possède des propriétés pour chacune des interfaces facultatives de l’objet rowset. Si le consommateur souhaite utiliser l’une de ces interfaces facultatives, il affecte à une propriété la valeur true. Le fournisseur peut ensuite vérifier cette propriété et prendre une mesure spéciale en fonction de celle-ci.

Dans votre implémentation, vous récupérez la propriété en utilisant le pointeur désignant l’objet Command. Le `pThis` pointeur représente l’ensemble de lignes ou la classe de commande. Étant donné que vous utilisez des modèles ici, vous devez le passer en tant que **`void`** pointeur ou le code ne se compile pas.

Spécifiez un tableau statique pour contenir les informations de colonne. Si le consommateur ne souhaite pas la colonne de signets, une entrée dans le tableau est gaspillée. Vous pouvez allouer dynamiquement ce tableau, mais vous devez veiller à le détruire correctement. Cet exemple définit et utilise les macros ADD_COLUMN_ENTRY et ADD_COLUMN_ENTRY_EX pour insérer les informations dans le tableau. Vous pouvez ajouter les macros à l’RS *personnalisé*. Fichier H comme indiqué dans le code suivant :

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

Pour tester le code dans le consommateur, vous devez apporter quelques modifications au `OnRun` Gestionnaire. La première modification de la fonction est que vous ajoutez du code pour ajouter une propriété au jeu de propriétés. Le code attribue `DBPROP_IRowsetLocate` à la propriété la valeur true, indiquant ainsi au fournisseur que vous souhaitez la colonne de signets. Le `OnRun` Code du gestionnaire doit se présenter comme suit :

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

La **`while`** boucle contient du code pour appeler la `Compare` méthode dans l' `IRowsetLocate` interface. Le code que vous avez doit toujours réussir, car vous comparez exactement les mêmes signets. En outre, stockez un signet dans une variable temporaire afin de pouvoir l’utiliser une fois la **`while`** boucle terminée pour appeler la `MoveToBookmark` fonction dans les modèles de consommateur. La `MoveToBookmark` fonction appelle la `GetRowsAt` méthode dans `IRowsetLocate` .

Vous devez également mettre à jour l’enregistrement utilisateur dans le consommateur. Ajoutez une entrée dans la classe pour gérer un signet et une entrée dans le COLUMN_MAP :

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Une fois que vous avez mis à jour le code, vous devez être en mesure de générer et d’exécuter le fournisseur avec l' `IRowsetLocate` interface.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)
