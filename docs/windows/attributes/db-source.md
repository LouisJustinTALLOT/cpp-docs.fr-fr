---
description: 'En savoir plus sur : db_source'
title: db_source (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 273d6626a8cd6fa2cadc42bac7ddb2e5e28a69c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333075"
---
# <a name="db_source"></a>db_source

Crée une connexion à une source de données.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Paramètres

*db_source*<br/>
Chaîne de connexion utilisée pour se connecter à la source de données. Pour plus d’informations sur le format de la chaîne de connexion, consultez [chaînes de connexion et liaisons de données](/previous-versions/windows/desktop/ms718376(v=vs.85)) dans le kit de développement logiciel (SDK) Microsoft Data Access Components (MDAC).

*name*<br/>
Facultatif Quand vous utilisez **db_source** sur une classe, *Name* est une instance d’un objet source de données auquel l’attribut **db_source** est appliqué (Voir l’exemple 1). Quand vous utilisez **db_source** inline dans une implémentation de méthode, le *nom* est une variable (locale à la méthode) qui peut être utilisée pour accéder à la source de données (Voir l’exemple 2). Vous transmettez ce *nom* au paramètre *source_name* de `db_command` pour associer la source de données à une commande.

*signé*<br/>
Facultatif Identifie la variable qui recevra le HRESULT de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.

## <a name="remarks"></a>Notes

**db_source** crée un [CDataSource](../../data/oledb/cdatasource-class.md) et un objet [CSession](../../data/oledb/csession-class.md) , qui représentent ensemble une connexion avec une source de données de consommateur OLE DB.

Quand vous utilisez **db_source** sur une classe, l' `CSession` objet devient un membre de la classe.

Quand vous utilisez **db_source** dans une méthode, le code injecté est exécuté dans la portée de la méthode, et l' `CSession` objet est créé en tant que variable locale.

**db_source** ajoute des propriétés de source de données à une classe ou dans une méthode. Elle est utilisée conjointement avec `db_command` (qui prend le paramètre de *nom* *db_source* comme paramètre *source_name* ).

Lorsque le fournisseur d’attributs du consommateur applique cet attribut à une classe, le compilateur renomme la classe en \_ accesseur *YourClassName*, où *YourClassName* est le nom que vous avez donné à la classe, et le compilateur crée également une classe appelée *YourClassName*, qui dérive de l' \_ accesseur *YourClassName*.  Dans l’affichage de classes, vous verrez les deux classes.

Pour obtenir un exemple de cet attribut utilisé dans une application, consultez [MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Exemple

Cet exemple appelle **db_source** sur une classe pour créer une connexion à la source de données à l' `ds` aide de la base de données Northwind. `ds` est un handle pour la source de données, qui peut être utilisé en interne avec la `CMyCommand` classe.

```cpp
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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`** , membre, méthode, local|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du consommateur OLE DB](ole-db-consumer-attributes.md)
