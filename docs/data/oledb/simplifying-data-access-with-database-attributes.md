---
title: Simplification de l'accès aux données à l'aide d'attributs de base de données
ms.date: 10/19/2018
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
ms.openlocfilehash: d22f8a25bc7bb58f72346a15edb51f062c44e1b4
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509461"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Simplification de l'accès aux données à l'aide d'attributs de base de données

Cette rubrique illustre l’utilisation d’attributs de base de données pour simplifier les opérations de base de données.

La méthode de base pour accéder à des informations à partir d’une base de données consiste à créer une classe de commande (ou de table) et une classe d’enregistrement utilisateur pour une table particulière dans la base de données. Les attributs de base de données simplifient certaines des déclarations de modèle que vous deviez auparavant faire.

Pour illustrer l’utilisation des attributs de base de données, les sections suivantes présentent deux déclarations équivalentes de la table et de la classe d’enregistrement utilisateur : la première utilise les attributs et la seconde utilise OLE DB modèles. Ce code de déclaration est généralement placé dans un fichier d’en-tête nommé pour la table ou l’objet de commande, par exemple authors. h.

En comparant les deux fichiers, vous pouvez voir combien il est plus simple d’utiliser des attributs. Parmi les différences, citons les suivantes :

- À l’aide d’attributs, il vous suffit de déclarer une classe : `CAuthors`, tandis que avec les modèles, vous devez déclarer deux : `CAuthorsNoAttrAccessor` et `CAuthorsNoAttr`.

- L’appel de `db_source` dans la version avec attributs est équivalent à l’appel de `OpenDataSource()` dans la déclaration de modèle.

- L’appel de `db_table` dans la version avec attributs est équivalent à la déclaration de modèle suivante :

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- Les appels de `db_column` dans la version avec attributs sont équivalents au mappage de colonnes (consultez `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) dans la déclaration de modèle.

Les attributs injectent une déclaration de classe d’enregistrement utilisateur pour vous. La classe d’enregistrement utilisateur est égale à `CAuthorsNoAttrAccessor` dans la déclaration de modèle. Si votre classe de table est `CAuthors`, la classe d’enregistrement utilisateur injectée est nommée `CAuthorsAccessor`et vous pouvez uniquement afficher sa déclaration dans le code injecté. Pour plus d’informations, consultez « classes d’enregistrement utilisateur injectées par les attributs » dans [enregistrements utilisateur](../../data/oledb/user-records.md).

Dans le code avec attributs et dans le code basé sur un modèle, vous devez définir les propriétés de l’ensemble de lignes à l’aide de `CDBPropSet::AddProperty`.

Pour plus d’informations sur les attributs décrits dans cette rubrique, consultez [OLE DB les attributs du consommateur](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Les instructions de `include` suivantes sont requises pour compiler les exemples ci-dessous :

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Déclaration de table et d’accesseur à l’aide d’attributs

Le code suivant appelle `db_source` et `db_table` sur la classe de table. `db_source` spécifie la source de données et la connexion à utiliser. `db_table` injecte le code de modèle approprié pour déclarer une classe de table. `db_column` spécifier le mappage de colonnes et injecter la déclaration d’accesseur. Vous pouvez utiliser OLE DB attributs de consommateur dans tout projet qui prend en charge ATL.

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
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>Déclaration de table et d’accesseur à l’aide de modèles

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
