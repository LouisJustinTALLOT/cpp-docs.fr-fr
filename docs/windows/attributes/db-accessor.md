---
title: db_accessor (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214862"
---
# <a name="db_accessor"></a>db_accessor

Groupes `db_column` attributs qui participent à la liaison basée sur `IAccessor`.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Paramètres

*num*<br/>
Spécifie le numéro d’accesseur (un index entier de base zéro). Vous devez spécifier des numéros d’accesseur par ordre croissant, en utilisant des entiers ou des valeurs définies.

*auto*<br/>
Valeur booléenne qui spécifie si l’accesseur est récupéré automatiquement (TRUE) ou non (FALSe).

## <a name="remarks"></a>Notes

**db_accessor** définit l’accesseur OLE DB sous-jacent pour les attributs `db_column` et `db_param` suivants dans la même classe ou la même fonction. **db_accessor** est utilisable au niveau du membre et est utilisé pour regrouper les attributs `db_column` qui participent à OLE DB liaison basée sur `IAccessor`. Il est utilisé conjointement avec les attributs `db_table` ou `db_command`. L’appel de cet attribut est semblable à l’appel des macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) .

**db_accessor** génère un ensemble de lignes et le lie aux mappages d’accesseur correspondants. Si vous n’appelez pas **db_accessor**, l’accesseur 0 est généré automatiquement, et toutes les liaisons de colonne sont mappées à ce bloc d’accesseur.

**db_accessor** groupe les liaisons de colonne de base de données dans un ou plusieurs accesseurs. Pour plus d’informations sur les scénarios dans lesquels vous devez utiliser plusieurs accesseurs, consultez [utilisation de plusieurs accesseurs sur un ensemble de lignes](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Consultez également la rubrique « prise en charge des enregistrements utilisateur pour plusieurs accesseurs » dans [enregistrements utilisateur](../../data/oledb/user-records.md).

Lorsque le fournisseur d’attributs du consommateur applique cet attribut à une classe, le compilateur renomme la classe en \_accesseur *YourClassName*, où *YourClassName* est le nom que vous avez donné à la classe, et le compilateur crée également une classe appelée *YourClassName*, qui dérive de \_accesseur *YourClassName*.  Dans l’affichage de classes, vous verrez les deux classes.

## <a name="example"></a>Exemple

L’exemple suivant utilise **db_accessor** pour regrouper des colonnes de la table Orders de la base de données Northwind en deux accesseurs. L’accesseur 0 est un accesseur automatique et l’accesseur 1 ne l’est pas.

```cpp
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
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)
