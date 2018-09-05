---
title: Simplifier l’accès aux données avec les attributs de base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9897be9bbcae0a03ef67996bda6f3ffbe894b8f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680450"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Simplification de l'accès aux données à l'aide d'attributs de base de données
Cette rubrique illustre l’utilisation d’attributs de base de données pour simplifier les opérations de base de données.  
  
 La méthode simple pour accéder aux informations à partir d’une base de données consiste à créer une classe de commande (ou table) et une classe d’enregistrement utilisateur pour une table particulière dans la base de données. Les attributs de base de données simplifient certaines des déclarations de modèles que vous deviez effectuer précédemment.  
  
 Pour illustrer l’utilisation d’attributs de base de données, les sections suivantes montrent deux table équivalente et les déclarations de classe d’enregistrement utilisateur : la première utilise les attributs et la seconde utilise les modèles OLE DB. Ce code de déclaration est généralement placé dans un fichier d’en-tête nommé pour l’objet table ou de la commande, par exemple, Authors.h.  
  
 En comparant les deux fichiers, vous pouvez voir comment beaucoup plus simple est d’utiliser les attributs. Parmi les différences sont :  
  
-   À l’aide des attributs, il vous suffit de déclarer une classe : `CAuthors`, tandis qu’avec des modèles, vous devez déclarer deux : `CAuthorsNoAttrAccessor` et `CAuthorsNoAttr`.  
  
-   Le `db_source` appel dans la version avec attributs est équivalent à la `OpenDataSource()` appeler dans la déclaration de modèle.  
  
-   Le `db_table` appel dans la version avec attributs est équivalent à la déclaration de modèle suivante :  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
    ```  
  
-   Le `db_column` appels dans la version avec attributs sont équivalents au mappage de colonnes (voir `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) dans la déclaration de modèle.  
  
 Les attributs injectent une déclaration de classe d’enregistrement utilisateur pour vous. La classe d’enregistrement utilisateur est équivalente à `CAuthorsNoAttrAccessor` dans la déclaration de modèle. Si votre classe de table est `CAuthors`, la classe d’enregistrement utilisateur injectée est nommée `CAuthorsAccessor`, et vous pouvez uniquement afficher sa déclaration dans le code injecté. Pour plus d’informations, consultez « Classes d’enregistrement utilisateur injectées par des attributs » dans [enregistrements utilisateur](../../data/oledb/user-records.md).  
  
 Notez que dans à la fois avec attributs et le code basé sur un modèle, vous devez définir les propriétés d’ensemble de lignes à l’aide `CDBPropSet::AddProperty`.  
  
 Pour plus d’informations sur les attributs présentés dans cette rubrique, consultez [les attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
## <a name="table-and-accessor-declaration-using-attributes"></a>Table et la déclaration d’accesseur à l’aide d’attributs  
 Le code suivant appelle `db_source` et `db_table` sur la classe de table. `db_source` Spécifie la source de données et la connexion à utiliser. `db_table` injecte le code de modèle approprié pour déclarer une classe de table. `db_column` spécifier le mappage de colonnes et injecte la déclaration d’accesseur. Vous pouvez utiliser des attributs du consommateur OLE DB dans n’importe quel projet qui prend en charge ATL.  
  
 Voici la déclaration de table et d’accesseur à l’aide d’attributs :  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// Table and accessor declaration using attributes  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// Table class declaration  
// (Note that you must provide your own connection string for db_source.)  
[  
   db_source(L"your connection string"),  
   db_table("Authors")  
]  
class CAuthors  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## <a name="table-and-accessor-declaration-using-templates"></a>Table et la déclaration d’accesseur à l’aide de modèles  
 Voici la déclaration de table et d’accesseur à l’aide de modèles.  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// Table and user record class declaration using templates  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// User record class declaration  
class CAuthorsNoAttrAccessor  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   LONG m_AuID;  
   TCHAR m_Author[51];  
   SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
   HRESULT OpenDataSource()  
   {  
      CDataSource _db;  

HRESULT hr;  
      hr = _db.OpenFromInitializationString(L"your connection string");  
      if (FAILED(hr))  
      {  
#ifdef _DEBUG  
         AtlTraceErrorRecords(hr);  
#endif  
         return hr;  
      }  
      return m_session.Open(_db);  
   }  
   void CloseDataSource()  
   {  
      m_session.Close();  
   }  
   operator const CSession&()  
   {  
      return m_session;  
   }  
   CSession m_session;  
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)  
   END_COLUMN_MAP()  
};  
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
{  
public:  
   HRESULT OpenAll()  
   {  
HRESULT hr;  
      hr = OpenDataSource();  
      if (FAILED(hr))  
         return hr;  
      __if_exists(GetRowsetProperties)  
      {  
         CDBPropSet propset(DBPROPSET_ROWSET);  
         __if_exists(HasBookmark)  
         {  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
         }  
         GetRowsetProperties(&propset);  
         return OpenRowset(&propset);  
      }  
      __if_not_exists(GetRowsetProperties)  
      {  
         __if_exists(HasBookmark)  
         {  
            CDBPropSet propset(DBPROPSET_ROWSET);  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
            return OpenRowset(&propset);  
         }  
      }  
      return OpenRowset();  
   }  
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
   {  
HRESULT hr = Open(m_session, "Authors", pPropSet);  
#ifdef _DEBUG  
      if(FAILED(hr))  
         AtlTraceErrorRecords(hr);  
#endif  
      return hr;  
   }  
   void CloseAll()  
   {  
      Close();  
      CloseDataSource();  
   }  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md)   
