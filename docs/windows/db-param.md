---
title: db_param | Microsoft Docs
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
ms.openlocfilehash: 6bfd96962cebd4b94e9b1b50ca588ada9af69779
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418383"
---
# <a name="dbparam"></a>db_param

Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.

## <a name="syntax"></a>Syntaxe

```cpp
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

### <a name="parameters"></a>Paramètres

*Ordinal*<br/>
Le numéro de colonne (ordinal DBCOLUMNINFO) correspondant à un champ dans l’ensemble de lignes à laquelle lier des données.

*ParamType*<br/>
(Facultatif) Le type à définir pour le paramètre. Fournisseurs prennent en charge uniquement les types de d’e/s de paramètres qui sont pris en charge par la source de données sous-jacente. Le type est une combinaison d’une ou plusieurs valeurs DBPARAMIOENUM :

- DBPARAMIO_INPUT un paramètre d’entrée.

- DBPARAMIO_OUTPUT un paramètre de sortie.

- DBPARAMIO_NOTPARAM l’accesseur n’a aucun paramètre. Paramètre `eParamIO` à cette valeur dans la ligne accesseurs rappelle à l’utilisateur que les paramètres sont ignorés.

*DbType*<br/>
(Facultatif) OLE DB [indicateur de Type](/previous-versions/windows/desktop/ms711251\(v=vs.85\)) pour l’entrée de la colonne.

*precision*<br/>
(Facultatif) La précision à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de `bPrecision` élément de la [structure DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*Mise à l’échelle*<br/>
(Facultatif) La mise à l’échelle à utiliser pour l’entrée de colonne. Pour plus d’informations, consultez la description de `bScale` élément de la [structure DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*status*<br/>
(Facultatif) Une variable de membre permet de conserver l’état de cette colonne. L’état indique si la valeur de colonne est une valeur de données ou une autre valeur, comme NULL. Pour connaître les valeurs possibles, consultez [état](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.

*length*<br/>
(Facultatif) Une variable de membre utilisée pour conserver la taille de la colonne en octets.

## <a name="remarks"></a>Notes

**db_param** définit les paramètres que vous utilisez dans les commandes ; par conséquent, utilisez-la avec `db_command`. Par exemple, vous pouvez utiliser **db_param** pour lier les paramètres dans les requêtes SQL ou des procédures stockées. Paramètres d’une procédure stockée sont indiqués par les points d’interrogation ( ?), et vous devez lier les membres de données dans l’ordre dans lequel les paramètres apparaissent.

**db_param** délimite les données membres qui peuvent participer à OLE DB `ICommandWithParameters`-en fonction de liaison. Il définit le type de paramètre (entrée ou sortie), type OLE DB, précision, échelle, état et de longueur pour le paramètre spécifié. Cet attribut insère les macros de consommateur OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Chaque membre que vous marquez avec le **db_param** attribut occupe une seule entrée dans la carte sous la forme d’un COLUMN_ENTRY.

**db_param** est utilisé conjointement avec soit le [db_table](../windows/db-table.md) ou [db_command](../windows/db-command.md) attributs.

Lorsque le fournisseur d’attributs consommateur applique cet attribut à une classe, le compilateur renomme la classe à \_ *Nom_de_votre_classe*accesseur, où *Nom_de_votre_classe* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *Nom_de_votre_classe*, qui dérive à son \_ *Nom_de_votre_classe*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.

## <a name="example"></a>Exemple

L’exemple suivant crée une classe de commande basée sur la procédure SalesbyYear stockée dans la base de données Northwind. Elle associe le premier paramètre dans la procédure stockée avec la `m_RETURN_VALUE` variable et la définit comme un paramètre de sortie. Elle associe les deux derniers paramètres (entrées) avec `m_Beginning_Date` et `m_Ending_Date`.

L’exemple suivant associe le `nOutput` variable avec un paramètre de sortie.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**, membre, méthode, locale|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)  
