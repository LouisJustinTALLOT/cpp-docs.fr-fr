---
description: 'En savoir plus sur : db_param'
title: db_param (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 27666b4cdf027e24b54326a3acc5fe701b9f6f44
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333111"
---
# <a name="db_param"></a>db_param

Associe la variable de membre spécifiée à un paramètre d’entrée ou de sortie et délimite la variable.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Paramètres

*formations*<br/>
Numéro de colonne (ordinal DBCOLUMNINFO) correspondant à un champ de l’ensemble de lignes auquel lier des données.

*type ParamType*<br/>
Facultatif Type à définir pour le paramètre. Les fournisseurs ne prennent en charge que les types d’e/s de paramètre pris en charge par la source de données sous-jacente. Le type est une combinaison d’une ou plusieurs valeurs DBPARAMIOENUM :

- DBPARAMIO_INPUT Paramètre d’entrée.

- DBPARAMIO_OUTPUT Paramètre de sortie.

- DBPARAMIO_NOTPARAM L’accesseur n’a aucun paramètre. `eParamIO`La définition de cette valeur dans les accesseurs de ligne rappelle à l’utilisateur que les paramètres sont ignorés.

*DbType*<br/>
Facultatif Indicateur de [Type](/previous-versions/windows/desktop/ms711251(v=vs.85)) OLE DB pour l’entrée de colonne.

*precision*<br/>
Facultatif Précision à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de l' `bPrecision` élément de la [Structure DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*scale*<br/>
Facultatif Échelle à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de l' `bScale` élément de la [Structure DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*statut*<br/>
Facultatif Variable membre utilisée pour contenir l’état de cette colonne. L’état indique si la valeur de la colonne est une valeur de données ou une autre valeur, telle que NULL. Pour connaître les valeurs possibles, consultez la section [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

*length*<br/>
Facultatif Variable membre utilisée pour contenir la taille de la colonne en octets.

## <a name="remarks"></a>Notes

**db_param** définit les paramètres que vous utilisez dans les commandes ; par conséquent, vous pouvez l’utiliser avec `db_command` . Par exemple, vous pouvez utiliser **db_param** pour lier des paramètres dans des requêtes SQL ou des procédures stockées. Les paramètres d’une procédure stockée sont dénotés par des points d’interrogation ( ?) et vous devez lier les membres de données dans l’ordre dans lequel les paramètres apparaissent.

**db_param** délimite les données membres qui peuvent participer à la `ICommandWithParameters` liaison basée sur OLE DB. Il définit le type de paramètre (entrée ou sortie), le type de OLE DB, la précision, l’échelle, l’État et la longueur du paramètre spécifié. Cet attribut insère les macros de OLE DB consommateur BEGIN_PARAM_MAP... END_PARAM_MAP. Chaque membre que vous marquez avec l’attribut **db_param** occupe une entrée de la carte sous la forme d’un COLUMN_ENTRY.

**db_param** est utilisé conjointement avec les attributs [db_table](db-table.md) ou [db_command](db-command.md) .

Lorsque le fournisseur d’attributs du consommateur applique cet attribut à une classe, le compilateur renomme la classe en \_ accesseur *YourClassName*, où *YourClassName* est le nom que vous avez donné à la classe, et le compilateur crée également une classe appelée *YourClassName*, qui dérive de l' \_ accesseur *YourClassName*.  Dans l’affichage de classes, vous verrez les deux classes.

## <a name="example"></a>Exemple

L’exemple suivant crée une classe Command basée sur la procédure stockée SalesbyYear dans la base de données Northwind. Il associe le premier paramètre de la procédure stockée à la `m_RETURN_VALUE` variable et le définit en tant que paramètre de sortie. Il associe les deux derniers paramètres (entrée) à `m_Beginning_Date` et `m_Ending_Date` .

L’exemple suivant associe la `nOutput` variable à un paramètre de sortie.

```cpp
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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`** , membre, méthode, local|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)
