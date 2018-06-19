---
title: db_accessor | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b81e55500a8ff44c887bed592c9472c5a8d3ea1d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874523"
---
# <a name="dbaccessor"></a>db_accessor
Groupes **db_column** attributs participer `IAccessor`-en fonction de liaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *num*  
 Spécifie le numéro de l’accesseur (un index entier de base zéro). Vous devez spécifier les numéros d’accesseur par ordre croissant de commande, à l’aide d’entiers ou valeurs définies.  
  
 *auto*  
 Valeur booléenne qui spécifie si l’accesseur est automatiquement récupéré (**TRUE**) ou pas récupérés (**FALSE**).  
  
## <a name="remarks"></a>Notes  
 **db_accessor** définit l’accesseur OLE DB sous-jacent pour ultérieures **db_column** et **db_param** attributs au sein de la même classe ou fonction. **db_accessor** est utilisable au niveau du membre et est utilisé pour le groupe **db_column** les attributs qui participent à OLE DB `IAccessor`-liaison basée sur. Il est utilisé conjointement avec l’option le **db_table** ou **db_command** attributs. Appel de cet attribut ressemble à appeler la [BEGIN_ACCESSOR](../data/oledb/begin-accessor.md) et [END_ACCESSOR](../data/oledb/end-accessor.md) macros.  
  
 **db_accessor** génère un ensemble de lignes et le lie aux mappages d’accesseur correspondant. Si vous n’appelez pas **db_accessor**accesseur 0 est automatiquement générée et toutes les liaisons de colonne seront mappées à ce bloc d’accesseur.  
  
 **db_accessor** liaisons de colonne dans un ou plusieurs accesseurs de la base de données des groupes. Pour en savoir plus sur les scénarios dans lesquels vous devez utiliser plusieurs accesseurs, consultez [à l’aide de plusieurs accesseurs sur un ensemble de lignes](../data/oledb/using-multiple-accessors-on-a-rowset.md). Consultez également « Utilisateur enregistrement prise en charge pour les accesseurs multiples » dans [enregistrements utilisateur](../data/oledb/user-records.md).  
  
 Lorsque le fournisseur de consommateur d’attribut s’applique à cet attribut à une classe, le compilateur attribue la classe à \_ *YourClassName*accesseur, où *YourClassName* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *YourClassName*, lequel dérive \_ *YourClassName*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise **db_accessor** pour grouper des colonnes dans la table Orders à partir de la base de données Northwind dans deux accesseurs. L’accesseur 0 est un accesseur automatique, et l’accesseur 1 n’est pas.  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Blocs d’attributs|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)   
