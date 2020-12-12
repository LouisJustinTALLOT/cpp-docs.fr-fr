---
description: 'En savoir plus sur : initialisation des types scalaires'
title: Initialisation des types scalaires
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: a9294f04f39e6984a2068c5c8f79e48641834236
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181824"
---
# <a name="initializing-scalar-types"></a>Initialisation des types scalaires

Lors de l’initialisation de types scalaires, la valeur de *`assignment-expression`* est assignée à la variable. Les règles de conversion pour l'assignation s'appliquent. (Consultez [Conversions de type](../c-language/type-conversions-c.md) pour plus d'informations sur les règles de conversion.)

## <a name="syntax"></a>Syntaxe

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`init-declarator-list`* <sub>OPT</sub>**`;`**

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>OPT</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>OPT</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`***`=`** *`initializer`* /\* Pour l’initialisation scalaire\*/

*`initializer`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assignment-expression`*

Vous pouvez initialiser des variables de tout type, à condition que vous respectiez les règles suivantes :

- Les variables déclarées au niveau de la portée du fichier peuvent être initialisées. Si vous n'initialisez pas explicitement une variable au niveau externe, elle est initialisée à 0 par défaut.

- Une expression constante peut être utilisée pour initialiser toute variable globale déclarée avec le **`static`** *`storage-class-specifier`* . Les variables déclarées comme étant **`static`** initialisées au début de l’exécution du programme. Si vous n’initialisez pas explicitement une **`static`** variable globale, elle est initialisée à 0 par défaut, et tous les membres qui ont un type pointeur se voient assigner un pointeur null.

- Les variables déclarées avec le **`auto`** **`register`** spécificateur de classe de stockage ou sont initialisées chaque fois que le contrôle d’exécution passe au bloc dans lequel elles sont déclarées. Si vous omettez un initialiseur à partir de la déclaration d’une **`auto`** **`register`** variable ou, la valeur initiale de la variable n’est pas définie. Pour les valeurs auto et register, l'initialiseur n'est pas simplement une constante. Il peut s'agir d'une expression utilisant des valeurs définies précédemment, même des appels de fonction.

- Les valeurs initiales pour les déclarations de variables externes et pour toutes les **`static`** variables, qu’elles soient externes ou internes, doivent être des expressions constantes. (Pour plus d’informations, consultez [expressions constantes](../c-language/c-constant-expressions.md).) Étant donné que l’adresse de toute variable statique ou déclarée de manière externe est constante, elle peut être utilisée pour initialiser une variable pointeur déclarée en interne **`static`** . Toutefois, l’adresse d’une **`auto`** variable ne peut pas être utilisée comme initialiseur statique, car elle peut être différente pour chaque exécution du bloc. Vous pouvez utiliser des valeurs constantes ou variables pour initialiser **`auto`** et des **`register`** variables.

- Si la déclaration d’un identificateur a une portée de bloc, et si l’identificateur a une liaison externe, la déclaration ne peut pas avoir d’initialisation.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent les initialisations :

```C
int x = 10;
```

La variable de type entier `x` est initialisée à l'expression constante `10`.

```C
register int *px = 0;
```

Le pointeur `px` est initialisé à 0, produisant un pointeur Null.

```C
const int c = (3 * 1024);
```

Cet exemple utilise une expression constante `(3 * 1024)` pour initialiser `c` une valeur de constante qui ne peut pas être modifiée en raison du **`const`** mot clé.

```C
int *b = &x;
```

Cette instruction initialise le pointeur `b` avec l'adresse d'une autre variable, `x`.

```C
int *const a = &z;
```

Le pointeur `a` est initialisé avec l'adresse d'une variable nommée `z`. Toutefois, étant donné qu’il s’agit d’un **`const`** , la variable `a` peut uniquement être initialisée, jamais modifiée. Elle pointe toujours vers le même emplacement.

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

La variable globale `GLOBAL` est déclarée au niveau externe. Elle a donc une durée de vie globale. La variable locale `LOCAL` a **`auto`** une classe de stockage et n’a qu’une adresse au cours de l’exécution de la fonction dans laquelle elle est déclarée. Par conséquent, la tentative d’initialisation de la **`static`** variable pointeur `lp` avec l’adresse de `LOCAL` n’est pas autorisée. La **`static`** variable pointeur `gp` peut être initialisée à l’adresse de `GLOBAL` , car cette adresse est toujours la même. De même, `*rp` peut être initialisé car `rp` est une variable locale et peut avoir un initialiseur non constant. Chaque fois que le bloc est écrit, `LOCAL` a une nouvelle adresse, qui est ensuite assignée à `rp`.

## <a name="see-also"></a>Voir aussi

[D’initialisation](../c-language/initialization.md)
