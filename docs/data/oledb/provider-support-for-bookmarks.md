---
title: Prise en charge de fournisseur de signets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b16605b8cd0b5855d7a6cc1f5ceac9f46ad495f4
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337629"
---
# <a name="provider-support-for-bookmarks"></a>Prise en charge des signets par le fournisseur
L’exemple de cette rubrique ajoute le `IRowsetLocate` interface pour la `CMyProviderRowset` classe. Dans presque tous les cas, vous commencez par ajouter une interface à un objet COM existant. Vous pouvez ensuite le tester en ajoutant plusieurs appels à partir de modèles du consommateur. L’exemple montre comment :  
  
-   Ajouter une interface à un fournisseur.  
  
-   Déterminer dynamiquement les colonnes à retourner au consommateur.  
  
-   Ajouter la prise en charge du signet.  
  
 L'interface `IRowsetLocate` hérite de l'interface `IRowset`. Pour ajouter le `IRowsetLocate` l’interface, héritent `CMyProviderRowset` de [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).  
  
 Ajout de la `IRowsetLocate` interface est un peu différente de la plupart des interfaces. Pour aligner la vtable, OLE DB modèles du fournisseur ont un paramètre de modèle pour gérer l’interface dérivée. Le code suivant montre la nouvelle liste d’héritage :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>>  
```  
  
 La quatrième, cinquième et sixième paramètres sont tous ajoutés. Cet exemple utilise les valeurs par défaut pour la quatrième et cinquième paramètres mais spécifient `IRowsetLocateImpl` comme sixième paramètre. `IRowsetLocateImpl` est une classe de modèle OLE DB qui prend deux paramètres de modèle : ils raccordent le `IRowsetLocate` interface pour la `CMyProviderRowset` classe. Pour ajouter la plupart des interfaces, vous pouvez ignorer cette étape et passer à la suivante. Uniquement les `IRowsetLocate` et `IRowsetScroll` interfaces doivent être traitées de cette façon.  
  
 Vous devez alors indiquer le `CMyProviderRowset` pour appeler `QueryInterface` pour le `IRowsetLocate` interface. Ajoutez la ligne `COM_INTERFACE_ENTRY(IRowsetLocate)` à la carte. La table d’interface pour `CMyProviderRowset` doit apparaître comme indiqué dans le code suivant :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>> _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Vous devez également raccorder votre table à la `CRowsetImpl` classe. Ajoutez la macro COM_INTERFACE_ENTRY_CHAIN pour raccorder la `CRowsetImpl` carte. En outre, créez un typedef appelé `RowsetBaseClass` qui contient les informations d’héritage. Ce typedef est arbitraire et peut être ignoré.  
  
 Enfin, gérez le `IColumnsInfo::GetColumnsInfo` appeler. Les macros PROVIDER_COLUMN_ENTRY vous utiliseriez normalement pour ce faire. Toutefois, un consommateur souhaiterez peut-être utiliser des signets. Vous devez être en mesure de modifier les colonnes que le fournisseur retourne selon que le consommateur demande un signet.  
  
 Pour gérer les `IColumnsInfo::GetColumnsInfo` appeler, supprimez le `PROVIDER_COLUMN` mapper dans le `CTextData` classe. La macro PROVIDER_COLUMN_MAP définit une fonction `GetColumnInfo`. Vous devez définir vos propres `GetColumnInfo` (fonction). La déclaration de fonction doit ressembler à ceci :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 Ensuite, implémentez la `GetColumnInfo` fonction dans le fichier MyProviderRS.cpp comme suit :  
  
```cpp
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
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
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
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
  
 `GetColumnInfo` premier vérifie si une propriété appelée `DBPROP_IRowsetLocate` est définie. OLE DB a des propriétés pour chacune des interfaces facultatives l’objet d’ensemble de lignes. Si le consommateur souhaite utiliser une de ces interfaces facultatives, il définit une propriété sur true. Le fournisseur peut ensuite vérifier cette propriété et prendre des mesures spéciales sur celui-ci.  
  
 Dans votre implémentation, vous obtenez la propriété à l’aide du pointeur vers l’objet de commande. Le `pThis` pointeur représente la classe rowset ou commande. Étant donné que vous utilisez des modèles ici, vous devez passer ceci comme un `void` pointeur ou le code n’est pas compilé.  
  
 Spécifiez un tableau statique pour contenir les informations de colonne. Si le consommateur ne souhaite pas que la colonne de signet, une entrée dans le tableau est gaspillée. Vous pouvez allouer dynamiquement de ce tableau, mais vous devez vous assurer d’éliminer correctement. Cet exemple définit et utilise les macros ADD_COLUMN_ENTRY et ADD_COLUMN_ENTRY_EX pour insérer les informations dans le tableau. Vous pouvez ajouter les macros au fichier MyProviderRS.H, comme indiqué dans le code suivant :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
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
  
 Pour tester le code dans le consommateur, vous devez apporter quelques modifications à la `OnRun` gestionnaire. La première modification à la fonction est d’ajouter le code pour ajouter une propriété au jeu de propriétés. Le code définit le `DBPROP_IRowsetLocate` propriété sur true, indiquant ainsi au fournisseur que vous voulez la colonne de signet. Le `OnRun` code du gestionnaire doit apparaître comme suit :  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
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
  
 Le pendant que la boucle contient le code pour appeler le `Compare` méthode dans le `IRowsetLocate` interface. Le code que vous avez doit toujours passer, car vous comparez exactement les mêmes signets. En outre, stockez un signet dans une variable temporaire afin que vous puissiez l’utiliser après le pendant que boucle a fini d’appeler le `MoveToBookmark` fonction dans les modèles du consommateur. Le `MoveToBookmark` appels de fonction le `GetRowsAt` méthode dans `IRowsetLocate`.  
  
 Vous devez également mettre à jour l’enregistrement d’utilisateur dans le consommateur. Ajouter une entrée dans la classe pour gérer un signet et une entrée dans le `COLUMN_MAP`:  
  
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
  
 Lorsque vous avez mis à jour le code, vous devez pouvoir générer et exécuter le fournisseur avec le `IRowsetLocate` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)