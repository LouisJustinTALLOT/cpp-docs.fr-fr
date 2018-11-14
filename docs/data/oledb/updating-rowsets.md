---
title: mettre à jour les jeux de lignes
ms.date: 10/19/2018
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: d00b9036b216e3425615478d6bf92d239a3637d1
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556697"
---
# <a name="updating-rowsets"></a>mettre à jour les jeux de lignes

Une opération de base de données consiste à mettre à jour, ou écrire des données dans le magasin de données. Dans OLE DB, le mécanisme de mise à jour est simple : votre application consommatrice définit les valeurs des membres de données liés, puis écrit ces valeurs dans le rowset ; le consommateur demande ensuite au fournisseur de mettre à jour le magasin de données.

Les consommateurs peuvent effectuer les types suivants de mises à jour sur les données de l’ensemble de lignes : définition des valeurs de colonne dans une ligne, insertion d’une ligne et la suppression d’une ligne. Pour effectuer ces opérations, la classe de modèle OLE DB [CRowset](../../data/oledb/crowset-class.md) implémente le [IRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715790(v=vs.85)) interface et substitue les méthodes d’interface suivantes :

- [SetData](../../data/oledb/crowset-setdata.md) les valeurs des colonnes de modifications dans une ligne d’un ensemble de lignes ; ce qui équivaut à la commande SQL UPDATE.

- [Insérer](../../data/oledb/crowset-insert.md) insère une ligne dans un rowset ; elle est égale à la commande SQL INSERT.

- [Supprimer](../../data/oledb/crowset-delete.md) supprime des lignes d’un rowset ; elle est égale à la commande SQL DELETE.

## <a name="supporting-update-operations"></a>Prise en charge des opérations de mise à jour

Lorsque vous créez un consommateur avec le **Assistant Consommateur OLE DB ATL**, vous pouvez prendre en charge les opérations de mise à jour en sélectionnant une ou plusieurs des trois cases à cocher **modification**, **insérer**, et **supprimer**. Si vous sélectionnez ces options, l’Assistant modifie le code de manière appropriée pour prendre en charge le type de modifications que vous choisissez. Toutefois, si vous n’utilisez pas l’Assistant, vous devez définir les propriétés d’ensemble de lignes suivantes `VARIANT_TRUE` pour prendre en charge les mises à jour :

- `DBPROPVAL_UP_CHANGE` vous permet de modifier les valeurs de données dans une ligne.

- `DBPROPVAL_UP_INSERT` vous permet d’insérer une ligne.

- `DBPROPVAL_UP_DELETE` vous permet de supprimer une ligne.

Vous définissez les propriétés comme suit :

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

Modification, insertion, opérations ou suppression peuvent échouer si une ou plusieurs colonnes n’est pas accessible en écriture. Modifier le mappage de votre curseur pour corriger ce problème.

## <a name="setting-data-in-rows"></a>Définition de données dans des lignes

[CRowset::SetData](../../data/oledb/crowset-setdata.md) définit les valeurs des données dans une ou plusieurs colonnes de la ligne actuelle. Le code suivant définit les valeurs des données membres liées aux colonnes `Name` et `Units in Stock` de la table `Products` , puis appelle `SetData` pour écrire ces valeurs dans la 100ième ligne du rowset :

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>Insertion de lignes dans des rowsets

[CRowset::Insert](../../data/oledb/crowset-insert.md) crée et initialise une ligne en utilisant les données provenant de l’accesseur. `Insert` Crée une ligne entièrement nouvelle après la ligne actuelle ; Vous devez spécifier s’il faut incrémenter la ligne actuelle à la ligne suivante ou la laisser inchangée. Pour cela, vous définissez le paramètre *bGetRow* :

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** (valeur par défaut) spécifie que la ligne suivante devient la ligne active (auquel cas elle pointe vers la ligne insérée).

- **true** Spécifie que la ligne actuelle reste où elle est.

Le code suivant définit les valeurs des données membres liées aux colonnes de la table `Products` , puis appelle `Insert` pour insérer une nouvelle ligne avec ces valeurs après la 100ième ligne du jeu de lignes. Il est recommandé de définir toutes les valeurs de colonne afin d’éviter des données non définies dans la nouvelle ligne :

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

Pour obtenir un exemple plus détaillé, consultez [CRowset::Insert](../../data/oledb/crowset-insert.md).

Pour plus d’informations sur la définition des données membres d’état et de longueur, consultez [Membres de données d’état des champs dans les accesseurs générés par un Assistant](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

## <a name="deleting-rows-from-rowsets"></a>Suppression de lignes dans les rowsets

[CRowset::Delete](../../data/oledb/crowset-delete.md) supprime la ligne active du rowset. Le code suivant appelle `Delete` pour supprimer la 100ième ligne du rowset :

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>Mises à jour immédiates et différées

Sauf indication contraire, les appels à la `SetData`, `Insert`, et `Delete` méthodes mettre immédiatement à jour le magasin de données. Vous pouvez cependant différer les mises à jour, afin que le consommateur stocke toutes les modifications dans un cache local, puis les transfère vers le magasin de données quand vous appelez une des méthodes de mise à jour suivantes :

- [CRowset::Update](../../data/oledb/crowset-update.md) transfère toutes les modifications en attente apportées à la ligne actuelle depuis la dernière extraction ou `Update` appeler sur celle-ci.

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) transfère toutes les modifications en attente apportées à toutes les lignes depuis la dernière extraction ou `Update` appeler sur celle-ci.

Mise à jour, que ceux utilisés par les méthodes de mise à jour, a une signification spécifique apporter des modifications sur commande et n’est pas confondre avec le code SQL **mettre à jour** commande (`SetData` équivaut à SQL **mettre à jour** commande) .

Mises à jour différées sont utiles, par exemple, dans le cas d’une série de transactions bancaires ; Si une transaction est annulée, vous pouvez annuler la modification, car vous n’envoyez pas la série de modifications jusqu'à une fois que le dernier message est validée. En outre, le fournisseur peut regrouper les modifications en un seul appel réseau, qui est plus efficace.

Pour prendre en charge les mises à jour différées, vous devez définir le `DBPROP_IRowsetChange` propriété, ainsi que les propriétés décrites dans **prenant en charge les opérations de mise à jour**:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

Lorsque vous appelez `Update` ou `UpdateAll`, les méthodes transfèrent les modifications du cache local pour le magasin de données, puis effacent le cache local. Étant donné que la mise à jour transfère les modifications uniquement pour la ligne actuelle, il est important que votre application effectue le suivi de ligne à la mise à jour et quand mettre à jour. L’exemple suivant montre comment mettre à jour deux lignes consécutives :

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

Pour garantir le transfert des modifications en attente, vous devez appeler `Update` avant de passer à une autre ligne. Cependant, si c’est fastidieux ou inefficace, par exemple quand votre application doit mettre à jour des centaines de lignes, vous pouvez utiliser `UpdateAll` pour mettre à jour toutes les lignes à la fois.

Par exemple, si le premier `Update` appel étaient manquants dans le code ci-dessus, la ligne 100 restera inchangée, tandis que la ligne 101 serait modifiée. Après cela, votre application devrait appeler `UpdateAll` ou bien revenir à la ligne 100 et appeler `Update` pour cette ligne à mettre à jour.

Enfin, une des principales raisons de différer des modifications est la possibilité de les annuler. L’appel à [CRowset::Undo](../../data/oledb/crowset-undo.md) rétablit l’état du cache local des modifications à l’état du magasin de données avant que les modifications aient été apportées. Il est important de noter que `Undo` pas de report sauvegarder l’état du cache local en une seule étape (l’état précédant uniquement la dernière modification) ; au lieu de cela, elle efface le cache local pour cette ligne. En outre, `Undo` affecte uniquement la ligne actuelle.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset, classe](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
