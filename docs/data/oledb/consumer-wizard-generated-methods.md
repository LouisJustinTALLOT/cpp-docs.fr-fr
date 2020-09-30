---
title: Méthodes de consommateur générées par l'Assistant
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: f3bcc799f2a9591cfe7b2fc364b03161b5c0da33
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500690"
---
# <a name="consumer-wizard-generated-methods"></a>Méthodes de consommateur générées par l'Assistant

::: moniker range="vs-2019"

L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement.

::: moniker-end

::: moniker range="<=vs-2017"

L’**Assistant Consommateur OLE DB ATL** et l’**Assistant Application MFC** génèrent certaines fonctions que vous devriez connaître. Certaines méthodes sont implémentées différemment dans les projets avec attributs et présentent donc quelques risques à prendre en compte. Chaque cas est expliqué ci-après. Pour plus d’informations sur l’affichage de code injecté, consultez [Débogage de code injecté](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` ouvre la source de données ainsi que les ensembles de lignes et active les signets s’ils sont disponibles.

- `CloseAll` ferme tous les ensembles de lignes et libère toutes les exécutions de commande.

- `OpenRowset` est appelé par `OpenAll` pour ouvrir l’ensemble de lignes ou des ensembles de lignes du consommateur.

- `GetRowsetProperties` récupère un pointeur pour l’ensemble de propriétés de l’ensemble de lignes qui permet de définir les propriétés.

- `OpenDataSource` ouvre la source de données à l’aide de la chaîne d’initialisation que vous avez spécifiée dans la boîte de dialogue **Propriétés des liaisons de données**.

- `CloseDataSource` ferme la source de données de manière appropriée.

## <a name="openall-and-closeall"></a>OpenAll et CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

L’exemple suivant montre comment vous pouvez appeler `OpenAll` et `CloseAll` lorsque vous exécutez la même commande plusieurs fois. Comparez l’exemple de code dans [CCommand::Close](./ccommand-class.md#close), qui montre une variation qui appelle `Close` et `ReleaseCommand` au lieu de `CloseAll`.

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>Remarques

Si vous définissez une méthode `HasBookmark`, le code `OpenAll` définit la propriété `DBPROP_IRowsetLocate`. Faites-le seulement si votre fournisseur prend en charge cette propriété.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` appelle cette méthode pour ouvrir l’ensemble de ligne ou les ensembles de lignes dans le consommateur. En règle générale, vous n’avez pas besoin d’appeler `OpenRowset`, sauf si vous souhaitez travailler avec plusieurs sources de données/sessions/ensembles de lignes. `OpenRowset` est déclaré dans la commande ou le fichier d’en-tête de classe de la table :

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

Les attributs implémentent cette méthode différemment. Cette version prend un objet de session et une chaîne de commande qui est définie par défaut la chaîne de commande spécifiée dans db_command, bien que vous puissiez en passer une différente. Si vous définissez une méthode `HasBookmark`, le code `OpenRowset` définit la propriété `DBPROP_IRowsetLocate`. Faites-le seulement si votre fournisseur prend en charge cette propriété.

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

Cette méthode récupère un pointeur pour l’ensemble de propriétés de l’ensemble de lignes. Vous pouvez utiliser ce pointeur pour définir des propriétés telles que `DBPROP_IRowsetChange`. `GetRowsetProperties` est utilisé comme suit dans la classe d’enregistrement utilisateur. Vous pouvez modifier ce code pour définir les propriétés de l’ensemble de lignes supplémentaires :

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Remarques

Vous ne devez pas définir une méthode `GetRowsetProperties` globale, car elle pourrait créer un conflit avec celle définie par l’Assistant. Il s’agit d’une méthode générée par l’Assistant que vous obtenez avec les projets basés sur des modèles et avec attributs. Les attributs n’injectent pas ce code.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource et CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Remarques

L’Assistant définit les méthodes `OpenDataSource` et `CloseDataSource`. `OpenDataSource` appelle [CDataSource::OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB à l’aide d’un Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
