---
title: Indirection et opérateurs d'adresse
ms.date: 02/16/2018
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
ms.openlocfilehash: 146f84c90aa56b5abf6ae5212c1729022cb7e4dc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343893"
---
# <a name="indirection-and-address-of-operators"></a>Indirection et opérateurs d'adresse

L’opérateur d’indirection unaire (__&#42;__) accède à une valeur indirectement via un pointeur. L’opérande doit être un type de pointeur. Le résultat de l'opération est la valeur adressée par l'opérande ; autrement dit, la valeur à l'adresse vers laquelle son opérande pointe. Le type du résultat est le type traité par l'opérande.

Le résultat de l’opérateur d’indirection est *type* si l’opérande est de type *pointeur-à-type*. Si l'opérande pointe vers une fonction, le résultat est un désignateur de fonction. S’il pointe vers un objet, le résultat est une lvalue qui désigne l’objet.

Si la valeur de pointeur n’est pas valide, le résultat de l’opérateur d’indirection est non défini. Voici certaines des conditions les plus courantes qui invalident une valeur de pointeur :

- Le pointeur est un pointeur null.

- Le pointeur spécifie l’adresse d’un objet après la fin de sa durée de vie (par exemple, un objet qui est devenu hors de portée ou qui est été désalloué) au moment de la référence.

- Le pointeur spécifie une adresse alignée de façon inappropriée pour le type de l'objet désigné.

- Le pointeur spécifie une adresse non utilisée par le programme en cours d'exécution.

L’opérateur unaire Address-of**&**() donne l’adresse de son opérande. L’opérande doit être soit une lvalue qui désigne un objet qui n’est pas déclaré __register__ et n’est pas un champ de bits, soit le résultat d’un opérateur __&#42;__ unaire ou un opérateur (__&#91;&#93;__) de déréférencement de tableau ou un désignateur de fonction. Le résultat est de type *pointeur-à-type* pour un opérande de type *type*.

Si l’opérande est le résultat d’un opérateur __&#42;__ unaire, aucun opérateur n’est évalué et le résultat est comme si les deux étaient omis. Le résultat n’est pas une lvalue et les contraintes sur les opérateurs s’appliquent toujours. Si l’opérande est le résultat d’un opérateur __&#91;&#93;__, ni l’opérateur __&__ ni l’opérateur __&#42;__ unaire impliqué par l’opérateur __&#91;&#93;__ ne sont évalués. Le résultat a le même effet que la suppression __&__ de l’opérateur et la modification de l' __+__ opérateur __&#91;&#93;__ en opérateur. Sinon, le résultat est un pointeur vers l’objet ou la fonction désignée par l’opérande.

## <a name="examples"></a>Exemples

Les exemples ci-dessous utilisent ces déclarations courantes :

```C
int *pa, x;
int a[20];
double d;
```

Cette instruction utilise l’opérateur d’adresse (**&**) pour prendre l’adresse du sixième élément du tableau. `a` Le résultat est stocké dans la variable pointeur `pa` :

```C
pa = &a[5];
```

L'opérateur d'indirection (__&#42;__) est utilisé dans cet exemple pour accéder à la valeur `int` à l'adresse stockée dans `pa`. La valeur est assignée à la variable de type entier `x` :

```C
x = *pa;
```

Cet exemple montre que le résultat de l’application de l’opérateur d’indirection à l’adresse de `x` équivaut à `x` :

```C
assert( x == *&x );
```

Cet exemple montre des moyens équivalents de déclarer un pointeur vers une fonction :

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Une fois que la fonction `roundup` est déclarée, deux pointeurs désignant `roundup` sont déclarés et initialisés. Le premier pointeur, `proundup`, est initialisé en utilisant uniquement le nom de la fonction, tandis que le second, `pround`, utilise l'opérateur d'adresse dans l'initialisation. Les initialisations sont équivalentes.

## <a name="see-also"></a>Voir aussi

[Opérateur d’indirection : &#42;](../cpp/indirection-operator-star.md)<br/>
[address-of, opérateur](../cpp/address-of-operator-amp.md)
