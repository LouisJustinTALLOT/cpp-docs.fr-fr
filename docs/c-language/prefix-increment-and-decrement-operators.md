---
title: Opérateurs préfixés d'incrémentation et de décrémentation
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
ms.openlocfilehash: 041c44829b8a267ca053dc85da0333e86db6b7b7
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151297"
---
# <a name="prefix-increment-and-decrement-operators"></a>Opérateurs préfixés d'incrémentation et de décrémentation

Les opérateurs unaires (`++` et **--**) sont appelés opérateurs d’incrémentation ou de décrémentation « préfixés » lorsqu’ils apparaissent avant l’opérande. L'incrémentation et la décrémentation suffixées ont une priorité plus élevée que l'incrémentation et la décrémentation préfixées. L’opérande doit être de type entier, flottant ou pointeur et doit être une expression lvalue modifiable (une expression sans l’attribut **const**). Le résultat est une l-value.

Lorsque l'opérateur apparaît avant son opérande, l'opérande est incrémenté ou décrémenté et sa nouvelle valeur est le résultat de l'expression.

Un opérande de type intégral ou virgule flottante est incrémenté ou décrémenté par la valeur 1 entière. Le type du résultat est identique au type d'opérande. Un opérande de type pointeur est incrémenté ou décrémenté par la taille de l'objet qu'il adresse. Un pointeur incrémenté pointe vers l'objet suivant. Un pointeur décrémenté pointe vers l'objet précédent.

## <a name="example"></a>Exemple

Cet exemple illustre l'opérateur de pré-décrémentation unaire :

```
if( line[--i] != '\n' )
    return;
```

Dans cet exemple, la variable `i` est décrémentée avant d'être utilisée comme indice sur `line`.

## <a name="see-also"></a>Voir aussi

[Opérateurs unaires C](../c-language/c-unary-operators.md)
