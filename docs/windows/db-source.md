---
title: db_source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b826e5d630b52062892001c26efda01b5c7293f4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873717"
---
# <a name="dbsource"></a>db_source
Crée une connexion à une source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_source(   
   db_source,   
   name,   
   hresult   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *db_source*  
 La chaîne de connexion utilisée pour se connecter à la source de données. Pour le format de la chaîne de connexion, consultez [les chaînes de connexion et des liaisons de données](https://msdn.microsoft.com/en-us/library/ms718376.aspx) dans le Kit de développement logiciel Microsoft données Access Components (MDAC).  
  
 *name* (facultatif)  
 Lorsque vous utilisez `db_source` sur une classe, *nom* est une instance d’un objet de source de données qui a le `db_source` attribut appliquée (voir l’exemple 1). Lorsque vous utilisez `db_source` inline dans une implémentation de méthode, *nom* est une variable (locale à la méthode) qui peut être utilisée pour accéder aux données source (voir l’exemple 2). Vous passez ce *nom* à la `source_name` paramètre de **db_command** pour associer la source de données avec une commande.  
  
 `hresult` (facultatif)  
 Identifie la variable qui reçoit le `HRESULT` de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.  
  
## <a name="remarks"></a>Notes  
 `db_source` Crée un [CDataSource](../data/oledb/cdatasource-class.md) et un [CSession](../data/oledb/csession-class.md) objet, qui représentent une connexion à une source de données du consommateur OLE DB.  
  
 Lorsque vous utilisez `db_source` sur une classe, le `CSession` objet devient un membre de la classe.  
  
 Lorsque vous utilisez `db_source` dans une méthode, le code injecté sera exécuté dans la portée de la méthode et le `CSession` objet est créé en tant que variable locale.  
  
 `db_source` Ajoute les propriétés de source de données à une classe ou d’une méthode. Il est utilisé conjointement avec **db_command** (qui prend la `db_source` *nom* paramètre en tant que son `source_name` paramètre).  
  
 Lorsque le fournisseur de consommateur d’attribut s’applique à cet attribut à une classe, le compilateur attribue la classe à \_ *YourClassName*accesseur, où *YourClassName* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *YourClassName*, lequel dérive \_ *YourClassName*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
 Pour obtenir un exemple de cet attribut utilisé dans une application, consultez les exemples [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409) et [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Exemple  
 Cet exemple appelle `db_source` sur une classe pour créer une connexion à la source de données `ds` à l’aide de la base de données Northwind. `ds` est un handle pour la source de données, ce qui peut être utilisé en interne sur la `CMyCommand` classe.  
  
```  
// db_source_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[  
  db_source(L"my_connection_string", name="ds"),  
  db_command(L"select * from Products")  
]  
class CMyCommand {};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`, member, method, local|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)   
