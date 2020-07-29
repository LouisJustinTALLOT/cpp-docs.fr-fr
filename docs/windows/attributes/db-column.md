---
title: db_column (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: b78fb081895b7a3e8f0e266810cd19d1b2792240
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222145"
---
# <a name="db_column"></a>db_column

Lie une colonne spécifiée à une variable dans l’ensemble de lignes.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Paramètres

*ordinal*<br/>
Numéro de colonne ordinale ( `DBCOLUMNINFO` ordinal) ou nom de colonne (chaîne ANSI ou Unicode) correspondant à un champ de l’ensemble de lignes auquel lier des données. Si vous utilisez des nombres, vous pouvez ignorer les ordinaux consécutifs (par exemple : 1, 2, 3, 5). Le nom peut contenir des espaces si le fournisseur OLE DB que vous utilisez le prend en charge. Par exemple, vous pouvez utiliser l’un des formats suivants :

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

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

**db_column** lie la colonne de table spécifiée à une variable dans l’ensemble de lignes. Elle délimite les données membres qui peuvent participer à la `IAccessor` liaison basée sur OLE DB. Cet attribut configure le mappage de colonnes normalement défini à l’aide des macros de consommateur OLE DB [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)et [COLUMN_ENTRY](../../data/oledb/column-entry.md). Ils manipulent la [Structure DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) OLE DB pour lier la colonne spécifiée. Chaque membre que vous marquez avec l’attribut **db_column** occupe une entrée dans le mappage de colonne sous la forme d’une entrée de colonne. Par conséquent, vous appelez cet attribut à l’emplacement où vous placez le mappage de colonnes, autrement dit, dans la classe de commande ou de table.

Utilisez **db_column** conjointement avec les attributs [db_table](db-table.md) ou [db_command](db-command.md) .

Lorsque le fournisseur d’attributs du consommateur applique cet attribut à une classe, le compilateur renomme la classe en \_ accesseur *YourClassName*, où *YourClassName* est le nom que vous avez donné à la classe, et le compilateur crée également une classe appelée *YourClassName*, qui dérive de l' \_ accesseur *YourClassName*.  Dans l’affichage de classes, vous verrez les deux classes.

Pour obtenir un exemple de cet attribut utilisé dans une application, consultez [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Exemple

Cet exemple lie une colonne d’une table à un **`long`** membre de données et spécifie des champs d’État et de longueur.

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

Cet exemple lie quatre colonnes à une **`long`** , une chaîne de caractères, un horodatage et un `DB_NUMERIC` entier, dans cet ordre.

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

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**`class`**, **`struct`** , membre, méthode|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)<br/>
[Attributs de classe](class-attributes.md)
