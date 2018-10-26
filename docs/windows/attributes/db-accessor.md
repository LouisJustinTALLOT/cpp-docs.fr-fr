---
title: db_accessor (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: aa63ca982f436b49787e542c4789390faa1d16a0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057021"
---
# <a name="dbaccessor"></a>db_accessor

Groupes `db_column` attributs participer `IAccessor`-en fonction de liaison.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Paramètres

*num*<br/>
Spécifie le nombre d’accesseur (un index d’entier de base zéro). Vous devez spécifier les numéros d’accesseur croissant classer, à l’aide des entiers ou valeurs définies.

*auto*<br/>
Valeur booléenne qui spécifie si l’accesseur est récupéré automatiquement (TRUE) ou non récupéré (FALSE).

## <a name="remarks"></a>Notes

**db_accessor** définit l’accesseur OLE DB sous-jacent pour suivantes `db_column` et `db_param` attributs au sein de la même classe ou fonction. **db_accessor** est utilisable au niveau de membre et est utilisé pour le groupe `db_column` attributs qui participent à OLE DB `IAccessor`-liaison basée sur. Il est utilisé conjointement avec soit le `db_table` ou `db_command` attributs. Appel de cet attribut est similaire à l’appel le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

**db_accessor** génère un ensemble de lignes et le lie aux mappages d’accesseur correspondant. Si vous n’appelez pas **db_accessor**accesseur 0 est automatiquement générée et toutes les liaisons de colonne seront mappées à ce bloc d’accesseur.

**db_accessor** liaisons de colonne dans un ou plusieurs accesseurs de la base de données des groupes. Pour une présentation des scénarios dans lesquels vous devez utiliser plusieurs accesseurs, consultez [à l’aide de plusieurs accesseurs sur un ensemble de lignes](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Consultez également « Utilisateur enregistrement prise en charge pour plusieurs accesseurs » dans [enregistrements utilisateur](../../data/oledb/user-records.md).

Lorsque le fournisseur d’attributs consommateur applique cet attribut à une classe, le compilateur renomme la classe à \_ *Nom_de_votre_classe*accesseur, où *Nom_de_votre_classe* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *Nom_de_votre_classe*, qui dérive à son \_ *Nom_de_votre_classe*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.

## <a name="example"></a>Exemple

L’exemple suivant utilise **db_accessor** pour grouper les colonnes dans la table Orders à partir de la base de données Northwind dans deux accesseurs. Accesseur 0 est un accesseur automatique, et l’accesseur 1 n’est pas.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Blocs d’attributs|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)