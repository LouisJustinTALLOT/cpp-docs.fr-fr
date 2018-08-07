---
title: db_column | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20c651c6e671c7c4895fc7dba85d16fdeb998ad5
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570699"
---
# <a name="dbcolumn"></a>db_column
Lie une colonne spécifiée à une variable dans l’ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Ordinal*  
 Numéro de colonne ordinal (`DBCOLUMNINFO` ordinale) ou nom de colonne (chaîne ANSI ou Unicode) correspondant à un champ dans l’ensemble de lignes à laquelle lier des données. Si vous utilisez des nombres, vous pouvez ignorer les ordinaux consécutifs (par exemple : 1, 2, 3, 5). Le nom peut contenir des espaces si le fournisseur OLE DB que vous utilisez le prend en charge. Par exemple, vous pouvez utiliser un des formats suivants :  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *DbType* (facultatif)  
 OLE DB [indicateur de Type](https://msdn.microsoft.com/library/ms711251.aspx) pour l’entrée de la colonne.  
  
 *précision* (facultatif)  
 La précision à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de la `bPrecision` élément de la [structure DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx)  
  
 *mise à l’échelle* (facultatif)  
 La mise à l’échelle à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de `bScale` élément de la [structure DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx)  
  
 *état* (facultatif)  
 Une variable de membre permet de conserver l’état de cette colonne. L’état indique si la valeur de colonne est une valeur de données ou une autre valeur, comme NULL. Pour connaître les valeurs possibles, consultez [état](https://msdn.microsoft.com/library/ms722617.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *longueur* (facultatif)  
 Une variable de membre utilisée pour conserver la taille de la colonne en octets.  
  
## <a name="remarks"></a>Notes  
 **db_column** lie la colonne de table spécifié à une variable dans l’ensemble de lignes. Délimite les données membres qui peuvent participer à OLE DB `IAccessor`-en fonction de liaison. Cet attribut définit le mappage de colonnes normalement défini par l’utilisation des macros de consommateur OLE DB [BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../data/oledb/end-column-map.md), et [COLUMN_ENTRY](../data/oledb/column-entry.md). Ces manipulent OLE DB [structure DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) pour lier la colonne spécifiée. Chaque membre que vous marquez avec le **db_column** attribut occupe une seule entrée dans le mappage de colonne sous la forme d’une entrée de colonne. Par conséquent, vous appelez cet attribut où vous placeriez le mappage de colonnes, autrement dit, dans la classe de commande ou de table.  
  
 Utilisez **db_column** conjointement avec soit le [db_table](../windows/db-table.md) ou [db_command](../windows/db-command.md) attributs.  
  
 Lorsque le fournisseur d’attributs consommateur applique cet attribut à une classe, le compilateur renomme la classe à \_ *Nom_de_votre_classe*accesseur, où *Nom_de_votre_classe* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *Nom_de_votre_classe*, qui dérive à son \_ *Nom_de_votre_classe*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
 Pour obtenir des exemples de cet attribut utilisé dans une application, consultez les exemples [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409), et [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Exemple  
 Cet exemple lie une colonne dans une table à une **long** membre de données et spécifie les champs état et de longueur.  
  
```cpp  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple lie les quatre colonnes pour un **long**, une chaîne de caractères, un horodatage et un `DB_NUMERIC` entier, dans cet ordre.  
  
```cpp  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**, membre, méthode|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   