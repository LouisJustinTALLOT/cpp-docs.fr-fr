---
title: Méthodes de consommateur générées par l’Assistant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a3f80d3e421701ac0612ddb2552d10d1eff1f02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056025"
---
# <a name="consumer-wizard-generated-methods"></a>Méthodes de consommateur générées par l'Assistant

L’Assistant Consommateur OLE DB ATL et l’Assistant Application MFC génèrent certaines fonctions dont vous devez connaître. Notez que certaines méthodes sont implémentées différemment dans les projets avec attributs, il y a quelques avertissements ; chaque cas sont couverte ci-après. Pour plus d’informations sur l’affichage de code injecté, consultez [Débogage de code injecté](/visualstudio/debugger/how-to-debug-injected-code).  
  
- `OpenAll` Ouvre la source de données, ensembles de lignes et Active les signets s’ils sont disponibles.  
  
- `CloseAll` Ferme tous les ensembles de lignes et libère toutes les exécutions de commande.  
  
- `OpenRowset` est appelée par OpenAll pour ouvrir l’ensemble de lignes ou des ensembles de lignes du consommateur.  
  
- `GetRowsetProperties` Récupère un pointeur vers le propriétés de jeu avec les propriétés peuvent être définies.  
  
- `OpenDataSource` Ouvre la source de données à l’aide de la chaîne d’initialisation que vous avez spécifié dans le **propriétés des liaisons de données** boîte de dialogue.  
  
- `CloseDataSource` Ferme la source de données de manière appropriée.  
  
## <a name="openall-and-closeall"></a>OpenAll et CloseAll  
  
```cpp  
HRESULT OpenAll();   

void CloseAll();  
```  
  
L’exemple suivant montre comment vous pouvez appeler `OpenAll` et `CloseAll` lorsque vous exécutez la même commande plusieurs fois. Comparez l’exemple de code dans [CCommand::Close](../../data/oledb/ccommand-close.md), qui montre une variation qui appelle `Close` et `ReleaseCommand` au lieu de `CloseAll`.  
  
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
  
## <a name="remarks"></a>Notes  

Notez que si vous définissez un `HasBookmark` (méthode), le `OpenAll` code définit la propriété DBPROP_IRowsetLocate ; Assurez-vous que vous ne le faire si votre fournisseur prend en charge cette propriété.  
  
## <a name="openrowset"></a>OpenRowset  
  
```cpp  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
`OpenAll` appelle cette méthode pour ouvrir les jeux de lignes dans le consommateur. En règle générale, vous n’avez pas besoin d’appeler `OpenRowset` , sauf si vous souhaitez travailler avec plusieurs sources de données/sessions/ensembles de lignes. `OpenRowset` est déclaré dans le fichier d’en-tête de classe commande ou de table :  
  
```  
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
  
Les attributs implémentent cette méthode différemment. Cette version prend un objet de session et une chaîne de commande par défaut est la chaîne de commande spécifiée dans db_command, bien que vous pouvez passer à une autre. Notez que si vous définissez un `HasBookmark` (méthode), le `OpenRowset` code définit la propriété DBPROP_IRowsetLocate ; Assurez-vous que vous ne le faire si votre fournisseur prend en charge cette propriété.  
  
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
  
Cette méthode récupère un pointeur vers le jeu de propriétés de l’ensemble de lignes ; Vous pouvez utiliser ce pointeur pour définir des propriétés telles que DBPROP_IRowsetChange. `GetRowsetProperties` est utilisé comme suit dans la classe d’enregistrement utilisateur. Vous pouvez modifier ce code pour définir les propriétés de l’ensemble de lignes supplémentaires :  
  
```cpp  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>Notes  

Vous ne devez pas définir un global `GetRowsetProperties` méthode, car il pourrait être en conflit avec celle définie par l’Assistant. Notez qu’il s’agit d’une méthode générée par l’Assistant que vous obtenez avec les projets basés sur des modèles et avec attributs ; les attributs n’injectent pas ce code.  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource et CloseDataSource  
  
```cpp  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>Notes  

L’Assistant définit les méthodes `OpenDataSource` et `CloseDataSource`; `OpenDataSource` appels [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## <a name="see-also"></a>Voir aussi  

[Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)