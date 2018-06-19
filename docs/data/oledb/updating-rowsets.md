---
title: Mise à jour des ensembles de lignes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ca0ef94ba6c60bd43e24672fe7db669a3930fd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112379"
---
# <a name="updating-rowsets"></a>mettre à jour les jeux de lignes
Une opération de base de données très simple consiste à mettre à jour ou à écrire des données dans le magasin de données. Dans OLE DB, le mécanisme de mise à jour est simple : votre application consommatrice définit les valeurs des membres de données liés, puis écrit ces valeurs dans le rowset ; le consommateur demande ensuite au fournisseur de mettre à jour le magasin de données.  
  
 Les consommateurs peuvent effectuer les types de mises à jour suivants sur les données du rowset : définition des valeurs des colonnes dans une ligne, insertion d’une ligne et suppression d’une ligne. Pour effectuer ces opérations, la classe de modèle OLE DB [CRowset](../../data/oledb/crowset-class.md) implémente l’interface [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) et remplace les méthodes suivantes de l’interface :  
  
-   [SetData](../../data/oledb/crowset-setdata.md) change les valeurs des colonnes dans une ligne d’un rowset ; elle est équivalente à la commande SQL UPDATE.  
  
-   [Insert](../../data/oledb/crowset-insert.md) insère une ligne dans un rowset ; elle est équivalente à la commande SQL INSERT.  
  
-   [Delete](../../data/oledb/crowset-delete.md) supprime une ligne d’un rowset ; elle est équivalente à la commande SQL DELETE.  
  
## <a name="supporting-update-operations"></a>Prise en charge des opérations de mise à jour  
 Quand vous créez un consommateur avec l’Assistant Consommateur OLE DB ATL, vous pouvez prendre en charge les opérations de mise à jour en cochant une ou plusieurs des trois cases à cocher **Modifier**, **Insérer**et **Supprimer**. Si vous cochez ces cases, l’Assistant modifie le code en conséquence, de façon à prendre en charge le type de modifications que vous choisissez. Cependant, si vous n’utilisez pas l’Assistant, vous devez définir les propriétés de rowset suivantes sur `VARIANT_TRUE` pour prendre en charge les mises à jour :  
  
-   **DBPROPVAL_UP_CHANGE** vous permet de modifier les valeurs des données dans une ligne.  
  
-   **DBPROPVAL_UP_INSERT** vous permet d’insérer une ligne.  
  
-   **DBPROPVAL_UP_DELETE** vous permet de supprimer une ligne.  
  
 Vous définissez les propriétés comme suit :  
  
```  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 Les opérations de modification, d’insertion ou de suppression peuvent échouer si une ou plusieurs colonnes ne sont pas accessibles en écriture. Modifier le mappage de votre curseur pour corriger ce problème.  
  
## <a name="setting-data-in-rows"></a>Définition de données dans des lignes  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) définit les valeurs des données dans une ou plusieurs colonnes de la ligne actuelle. Le code suivant définit les valeurs des membres de données liés aux colonnes "Name" et "Units in Stock" de la table Products, puis appelle `SetData` pour écrire ces valeurs dans la 100ième ligne du rowset :  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_UnitsInStock = 10000;  
  
// Set the data  
HRESULT hr = product.SetData();  
```  
  
## <a name="inserting-rows-into-rowsets"></a>Insertion de lignes dans des rowsets  
 [CRowset::Insert](../../data/oledb/crowset-insert.md) crée et initialise une ligne en utilisant les données provenant de l’accesseur. **Insert** crée une ligne entièrement nouvelle après la ligne active ; vous devez spécifier si vous voulez faire passer la ligne active à la ligne suivante ou la laisser inchangée. Pour cela, vous définissez le paramètre *bGetRow* :  
  
```  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **false** (valeur par défaut) spécifie que la ligne suivante devient la ligne active (auquel cas elle pointe vers la ligne insérée).  
  
-   **true** spécifie que la ligne active reste où elle est.  
  
 Le code suivant définit les valeurs des membres de données liés aux colonnes de la table Products, puis appelle **Insert** pour insérer une nouvelle ligne avec ces valeurs après la 100ième ligne du rowset. Il est recommandé de définir toutes les valeurs des colonnes afin d’éviter des données non définies dans la nouvelle ligne :  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  

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
 [CRowset::Delete](../../data/oledb/crowset-delete.md) supprime la ligne active du rowset. Le code suivant appelle **Delete** pour supprimer la 100ième ligne du rowset :  
  
```  
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
 Sauf indication contraire, les appels aux méthodes `SetData`, **Insert**et **Delete** mettent à jour le magasin de données immédiatement. Vous pouvez cependant différer les mises à jour, afin que le consommateur stocke toutes les modifications dans un cache local, puis les transfère vers le magasin de données quand vous appelez une des méthodes de mise à jour suivantes :  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) transfère toutes les modifications en attente apportées à la ligne active depuis la dernière extraction ou depuis le dernier appel de **Update** sur cette ligne.  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) transfère toutes les modifications en attente apportées à toutes les lignes depuis la dernière extraction ou depuis le dernier appel de **Update** .  
  
 Notez que cette mise à jour, telle qu’elle est utilisée par les méthodes de mise à jour, consiste à apporter des modifications sur commande ; elle ne doit pas être confondue avec la commande SQL UPDATE (`SetData` est équivalente à la commande SQL UPDATE).  
  
 Les mises à jour différées sont utiles par exemple dans les cas d’une série de transactions bancaires : si une transaction est annulée, vous pouvez annuler la modification, car vous n’envoyez pas la série de modifications tant que la dernière n’est pas validée. En outre, le fournisseur peut regrouper les modifications en un seul appel réseau, qui est plus efficace.  
  
 Pour prendre en charge les mises à jour différées, vous devez définir la propriété **DBPROP_IRowsetChange** en plus des propriétés décrites dans « Prise en charge des opérations de mise à jour » :  
  
```  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 Quand vous appelez **Update** ou `UpdateAll`, les méthodes transfèrent les modifications du cache local vers le magasin de données, puis effacent le cache local. Étant donné que la mise à jour transfère les modifications seulement pour la ligne active, il est important que votre application fasse le suivi de la ligne à mettre à jour et du moment où elle doit être mise à jour. L’exemple suivant montre comment mettre à jour deux lignes consécutives :  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  

product.m_UnitsInStock = 10000;  

HRESULT hr = product.SetData();  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext();  

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  

product.m_UnitsInStock = 500;  

HRESULT hr = product.SetData();  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
 Pour que les modifications en attente soient effectivement transférées, vous devez appeler **Update** avant de passer à une autre ligne. Cependant, si c’est fastidieux ou inefficace, par exemple quand votre application doit mettre à jour des centaines de lignes, vous pouvez utiliser `UpdateAll` pour mettre à jour toutes les lignes à la fois.  
  
 Par exemple, si le premier appel à **Update** ne se trouvait pas dans le code ci-dessus, la ligne 100 resterait inchangée, alors que la ligne 101 serait modifiée. Après cela, votre application devrait appeler `UpdateAll` , ou bien revenir à la ligne 100 et appeler **Update** pour que cette ligne soit mise à jour.  
  
 Enfin, une des principales raisons de différer des modifications est la possibilité de les annuler. L’appel à [CRowset::Undo](../../data/oledb/crowset-undo.md) rétablit l’état du cache local des modifications à l’état du magasin de données avant que les modifications aient été apportées. Il est important de noter que **Undo** ne restaure pas l’état du cache local à l’étape immédiatement précédente (c’est-à-dire seulement à l’état précédant la dernière modification) ; au lieu de cela, elle efface le cache local pour cette ligne. En outre, **Undo** affecte seulement la ligne active.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [CRowset (classe)](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)