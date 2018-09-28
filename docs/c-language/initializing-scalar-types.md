---
title: Initialisation des types scalaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe692b6eb1d29492605e7a6d2e7d6839a3a33b71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754590"
---
# <a name="initializing-scalar-types"></a>Initialisation des types scalaires

Lors de l'initialisation de types scalaires, la valeur de *assignment-expression* est assignée à la variable. Les règles de conversion pour l'assignation s'appliquent. (Consultez [Conversions de type](../c-language/type-conversions-c.md) pour plus d'informations sur les règles de conversion.)

## <a name="syntax"></a>Syntaxe

*declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer* /\* Pour l’initialisation scalaire\*/

*initializer* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*

Vous pouvez initialiser des variables de tout type, à condition que vous respectiez les règles suivantes :

- Les variables déclarées au niveau de la portée du fichier peuvent être initialisées. Si vous n'initialisez pas explicitement une variable au niveau externe, elle est initialisée à 0 par défaut.

- Une expression constante peut être utilisée pour initialiser une variable globale déclarée avec le *storage-class-specifier* **static**. Les variables déclarées comme étant **static** sont initialisées lorsque l'exécution du programme démarre. Si vous n'initialisez pas explicitement une variable globale **static**, elle est initialisée à 0 par défaut, et un pointeur null est assigné à chaque membre de type pointeur.

- Les variables déclarées avec le spécificateur de classe de stockage **auto** ou **register** sont initialisées chaque fois que le contrôle d'exécution passe au bloc dans lequel elles sont déclarées. Si vous omettez un initialiseur à partir de la déclaration d'une variable **auto** ou **register**, la valeur initiale de la variable est indéfinie. Pour les valeurs auto et register, l'initialiseur n'est pas simplement une constante. Il peut s'agir d'une expression utilisant des valeurs définies précédemment, même des appels de fonction.

- Les valeurs initiales pour les déclarations de variables externes et pour toutes les variables **static**, qu'elles soient externes ou internes, doivent être des expressions constantes. (Pour plus d'informations, consultez [Expressions constantes](../c-language/c-constant-expressions.md).) Étant donné que l'adresse de toute variable statique ou déclarée extérieurement est constante, elle peut être utilisée pour initialiser une variable pointeur **static** déclarée en interne. Toutefois, l'adresse d'une variable **auto** ne peut pas être utilisée comme initialiseur statique, car elle peut être différente pour chaque exécution du bloc. Vous pouvez utiliser des valeurs constantes ou variables pour initialiser les variables **auto** et **register**.

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

Cet exemple utilise une expression constante `(3 * 1024)` pour initialiser `c` à une valeur de constante qui ne peut pas être modifiée en raison du mot clé **const**.

```C
int *b = &x;
```

Cette instruction initialise le pointeur `b` avec l'adresse d'une autre variable, `x`.

```C
int *const a = &z;
```

Le pointeur `a` est initialisé avec l'adresse d'une variable nommée `z`. Toutefois, étant donné qu'elle est spécifiée comme étant **const**, la variable `a` peut seulement être initialisée, mais ne peut jamais être modifiée. Elle pointe toujours vers le même emplacement.

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

La variable globale `GLOBAL` est déclarée au niveau externe. Elle a donc une durée de vie globale. La variable locale `LOCAL` a une classe de stockage **auto** et a une adresse seulement pendant l'exécution de la fonction dans laquelle elle est déclarée. Par conséquent, il n'est pas autorisé de tenter d'initialiser la variable pointeur **static** `lp` avec l'adresse de `LOCAL`. La variable pointeur **static** `gp` peut être initialisée à l'adresse de `GLOBAL`, car cette adresse ne varie pas. De même, `*rp` peut être initialisé car `rp` est une variable locale pouvant avoir un initialiseur non constant. Chaque fois que le bloc est écrit, `LOCAL` a une nouvelle adresse, qui est ensuite assignée à `rp`.

## <a name="see-also"></a>Voir aussi

[Initialisation](../c-language/initialization.md)