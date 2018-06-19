---
title: db_param | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7cf5c8e92e7fd6e6e10d7bef0519b1ced4cf62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880691"
---
# <a name="dbparam"></a>db_param
Associe la variable membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ordinal`  
 Le numéro de colonne (**DBCOLUMNINFO** ordinale) correspondant à un champ dans l’ensemble de lignes auquel vous souhaitez lier des données.  
  
 *ParamType* (facultatif)  
 Type à définir pour le paramètre. Fournisseurs prennent en charge uniquement les types d’e/s paramètre sont pris en charge par la source de données sous-jacente. Le type est une combinaison d’une ou plusieurs **DBPARAMIOENUM** valeurs :  
  
-   **DBPARAMIO_INPUT** Paramètre d’entrée.  
  
-   **DBPARAMIO_OUTPUT** Paramètre de sortie.  
  
-   **DBPARAMIO_NOTPARAM** L’accesseur n’a aucun paramètre. Paramètre **eParamIO** cette valeur dans la ligne accesseurs rappelle à l’utilisateur que les paramètres sont ignorés.  
  
 *DbType* (facultatif)  
 OLE DB [indicateur de Type](https://msdn.microsoft.com/en-us/library/ms711251.aspx) pour l’entrée de la colonne.  
  
 *précision* (facultatif)  
 La précision à utiliser pour l’entrée de la colonne. Pour plus d’informations, consultez la description de **bPrecision** élément de la [structure DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *mise à l’échelle* (facultatif)  
 L’échelle à utiliser pour l’entrée de la colonne. Pour plus d’informations, consultez la description de **bScale** élément de la [structure DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *état* (facultatif)  
 Une variable de membre utilisée pour stocker l’état de cette colonne. L’état indique si la valeur de colonne est une valeur de données ou une autre valeur, tel que **NULL**. Pour les valeurs possibles, consultez [état](https://msdn.microsoft.com/en-us/library/ms722617.aspx) dans les *de référence du programmeur OLE DB*.  
  
 *longueur* (facultatif)  
 Une variable de membre utilisée pour contenir la taille de la colonne en octets.  
  
## <a name="remarks"></a>Notes  
 **db_param** définit les paramètres que vous utilisez dans les commandes ; par conséquent, vous utilisez avec **db_command**. Par exemple, vous pouvez utiliser **db_param** pour lier les paramètres dans les requêtes SQL ou des procédures stockées. Paramètres d’une procédure stockée sont définis par des points d’interrogation ( ?), et vous devez lier les membres de données dans l’ordre dans lequel les paramètres apparaissent.  
  
 **db_param** délimite les données membres qui peuvent être utilisées dans OLE DB `ICommandWithParameters`-en fonction de liaison. Il définit le type de paramètre (entrée ou sortie), de type OLE DB, précision, échelle, état et de longueur pour le paramètre spécifié. Cet attribut insère les macros de consommateur OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Chaque membre que vous marquez avec la **db_param** attribut occupera une entrée dans le mappage sous la forme d’un COLUMN_ENTRY.  
  
 **db_param** est utilisé conjointement avec l’option le [db_table](../windows/db-table.md) ou [db_command](../windows/db-command.md) attributs.  
  
 Lorsque le fournisseur de consommateur d’attribut s’applique à cet attribut à une classe, le compilateur attribue la classe à \_ *YourClassName*accesseur, où *YourClassName* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *YourClassName*, lequel dérive \_ *YourClassName*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une classe de commande basée sur la procédure SalesbyYear stockée dans la base de données Northwind. Il associe le premier paramètre de la procédure stockée avec la `m_RETURN_VALUE` variable et la définit comme un paramètre de sortie. Elle associe les deux derniers paramètres (entrées) avec `m_Beginning_Date` et `m_Ending_Date`.  
  
 L’exemple suivant associe le `nOutput` variable avec un paramètre de sortie.  
  
```  
// db_param.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_source(L"my_connection_string"),   
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")   
]  
struct CSalesbyYear {  
   DBSTATUS m_dwShippedDateStatus;  
   DBSTATUS m_dwOrderIDStatus;  
   DBSTATUS m_dwSubtotalStatus;  
   DBSTATUS m_dwYearStatus;  
  
   DBLENGTH m_dwShippedDateLength;  
   DBLENGTH m_dwOrderIDLength;  
   DBLENGTH m_dwSubtotalLength;  
   DBLENGTH m_dwYearLength;  
  
   // Bind columns  
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;  
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;  
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;  
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];  
  
   // Bind parameters  
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;  
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;  
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;  
};  
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
