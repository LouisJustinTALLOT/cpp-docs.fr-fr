---
description: En savoir plus sur les déclarations de pointeur
title: Déclarations de pointeur
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 3c1670d1dd86e7df7f164e357ff99f3ed31e7339
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195916"
---
# <a name="pointer-declarations"></a>Déclarations de pointeur

Une *déclaration de pointeur* nomme une variable de pointeur et spécifie le type de l’objet vers lequel pointe la variable. Une variable déclarée comme pointeur contient une adresse mémoire.

## <a name="syntax"></a>Syntaxe

*déclarateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *déclarateur* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constante-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *Parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-List*<sub>OPT</sub> **)**

*pointeur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List-*<sub></sub> *pointeur* opt

*type-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*qualificateur de type*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

Le *type-specifier* donne le type de l’objet, qui peut être tout type base, structure ou union. Les variables pointeur peuvent également pointer vers des fonctions, des tableaux et d'autres pointeurs. Pour plus d’informations sur la déclaration et l’interprétation des types pointeur plus complexes, consultez [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).

En créant le *type-specifier* **`void`** , vous pouvez différer la spécification du type auquel le pointeur fait référence. Ce type d’élément est appelé « pointeur vers **`void`** » et est écrit sous la forme `void *` . Une variable déclarée comme pointeur vers *void* peut être utilisée pour indiquer un objet de tout type. Toutefois, pour exécuter la plupart des opérations sur le pointeur ou sur l'objet vers lequel il pointe, le type vers lequel il pointe doit être spécifié explicitement pour chaque opération. (Variables de type **`char`** <strong>\*</strong> et le type **`void`** <strong>\*</strong> sont compatibles avec l’assignation sans cast de type.) Une telle conversion peut être effectuée avec un cast de type (consultez [conversions de cast de type](../c-language/type-cast-conversions.md) pour plus d’informations).

Le *qualificateur de type* peut être **`const`** ou **`volatile`** , ou les deux. Ils spécifient, respectivement, que le pointeur ne peut pas être modifié par le programme lui-même ( **`const`** ), ou que le pointeur peut légitimement être modifié par un processus au-delà du contrôle du programme ( **`volatile`** ). (Pour plus d’informations sur et, consultez [qualificateurs de type](../c-language/type-qualifiers.md) **`const`** **`volatile`** .)

*declarator* nomme la variable et peut inclure un modificateur de type. Par exemple, si *declarator* représente un tableau, le type du pointeur est modifié et remplacé par un pointeur vers un tableau.

Vous pouvez déclarer un pointeur vers une structure, une union ou un type d'énumération avant de définir la structure, l'union ou le type d'énumération. Vous devez déclarer le pointeur à l'aide de la balise structure ou union comme indiqué dans les exemples ci-dessous. Ces déclarations sont autorisées car le compilateur n'a pas besoin de connaître la taille de la structure ou de l'union pour allouer l'espace pour la variable pointeur.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent les déclarations de pointeur.

```
char *message; /* Declares a pointer variable named message */
```

Le pointeur de *message* pointe vers une variable de **`char`** type.

```
int *pointers[10];  /* Declares an array of pointers */
```

Le tableau de *pointeurs* comporte 10 éléments ; chaque élément est un pointeur vers une variable de **`int`** type.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

Le variable *pointer* pointe vers un tableau de 10 éléments. Chaque élément de ce tableau a le **`int`** type.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

Le pointeur *x* peut être modifié pour pointer vers une autre **`int`** valeur, mais la valeur vers laquelle il pointe ne peut pas être modifiée.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

La variable *y* dans ces déclarations est déclarée comme pointeur constant vers une **`int`** valeur. La valeur qu’elle indique peut être modifiée, mais le pointeur doit toujours indiquer le même emplacement : l’adresse de *fixed_object*. De même, *z* est un pointeur constant, mais il est également déclaré pour pointer vers un **`int`** dont la valeur ne peut pas être modifiée par le programme. Le spécificateur supplémentaire **`volatile`** indique que même si la valeur de **const int** vers laquelle pointe *z* ne peut pas être modifiée par le programme, elle peut légitimement être modifiée par un processus s’exécutant en même temps que le programme. La déclaration de *w* spécifie que le programme ne peut pas modifier la valeur désignée et que le programme ne peut pas modifier le pointeur.

```
struct list *next, *previous; /* Uses the tag for list */
```

Cet exemple déclare deux variables pointeur, *next* et *previous*, qui indiquent le type de structure *list*. Cette déclaration peut apparaître avant la définition du type de structure *list* (voir l’exemple suivant), tant que la définition de type *list* a la même visibilité que la déclaration.

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

La variable *line* a le type de structure nommé *list*. Le type de structure de *liste* a trois membres : le premier membre est un pointeur vers une **`char`** valeur, le deuxième est une **`int`** valeur et le troisième est un pointeur vers une autre structure de *liste* .

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

L' *enregistrement* de la variable a le type de structure *ID*. Notez que *pname* est déclaré en tant que pointeur vers un autre type de structure nommé *Name*. Cette déclaration peut apparaître avant que le type *name* soit défini.

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)
