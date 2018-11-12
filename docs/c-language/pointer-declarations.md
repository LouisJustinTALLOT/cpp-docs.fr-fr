---
title: Déclarations de pointeur
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: c09e73eec0f020ccc334d443248feb09631a0f7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432466"
---
# <a name="pointer-declarations"></a>Déclarations de pointeur

Une *déclaration de pointeur* nomme une variable de pointeur et spécifie le type de l’objet vers lequel pointe la variable. Une variable déclarée comme pointeur contient une adresse mémoire.

## <a name="syntax"></a>Syntaxe

*declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**

*pointer* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

Le *type-specifier* donne le type de l’objet, qui peut être tout type base, structure ou union. Les variables pointeur peuvent également pointer vers des fonctions, des tableaux et d'autres pointeurs. Pour plus d’informations sur la déclaration et l’interprétation des types pointeur plus complexes, consultez [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).

En définissant le *type-specifier* sur **void**, vous pouvez différer la spécification du type auquel le pointeur se rapporte. Cet élément est appelé « pointeur vers **void** » et s’écrit `void *`. Une variable déclarée comme pointeur vers *void* peut être utilisée pour indiquer un objet de tout type. Toutefois, pour exécuter la plupart des opérations sur le pointeur ou sur l'objet vers lequel il pointe, le type vers lequel il pointe doit être spécifié explicitement pour chaque opération. Les variables de type **char** <strong>\*</strong> et de type **void** <strong>\*</strong> sont compatibles pour l’assignation sans cast de type. Cette conversion peut être effectuée avec un cast de type (pour plus d’informations, consultez [Conversions de cast de type](../c-language/type-cast-conversions.md)).

Le *type-qualifier* peut être **const** ou **volatile** ou les deux. Ils spécifient, respectivement, que le pointeur ne peut pas être modifié par le programme lui-même (**const**) ou que le pointeur peut légitimement être modifié par un processus en dehors du contrôle du programme (**volatile**). Pour plus d’informations sur **const** et **volatile**, consultez [Qualificateurs de type](../c-language/type-qualifiers.md).

*declarator* nomme la variable et peut inclure un modificateur de type. Par exemple, si *declarator* représente un tableau, le type du pointeur est modifié et remplacé par un pointeur vers un tableau.

Vous pouvez déclarer un pointeur vers une structure, une union ou un type d'énumération avant de définir la structure, l'union ou le type d'énumération. Vous devez déclarer le pointeur à l'aide de la balise structure ou union comme indiqué dans les exemples ci-dessous. Ces déclarations sont autorisées car le compilateur n'a pas besoin de connaître la taille de la structure ou de l'union pour allouer l'espace pour la variable pointeur.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent les déclarations de pointeur.

```
char *message; /* Declares a pointer variable named message */
```

Le pointeur *message* pointe vers une variable de type **char**.

```
int *pointers[10];  /* Declares an array of pointers */
```

Le tableau *pointers* contient 10 éléments ; chaque élément est un pointeur vers une variable de type **int**.

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

Le variable *pointer* pointe vers un tableau de 10 éléments. Chaque élément de ce tableau a le type **int**.

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

Le pointeur *x* peut être modifié pour pointer vers une valeur **int** différente, mais la valeur vers laquelle il pointe ne peut pas être modifiée.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

La variable *y* dans ces déclarations est déclarée comme pointeur constant vers une valeur **int**. La valeur qu’elle indique peut être modifiée, mais le pointeur doit toujours indiquer le même emplacement : l’adresse de *fixed_object*. De même, *z* est un pointeur constant, mais il est également déclaré pour pointer vers un **int** dont la valeur ne peut pas être modifiée par le programme. Le spécificateur supplémentaire **volatile** indique que bien que la valeur **const int** qui est indiquée par *z* ne puisse pas être modifiée par le programme, elle peut légitimement être modifiée par un processus en même temps que le programme. La déclaration de *w* spécifie que le programme ne peut pas modifier la valeur désignée et que le programme ne peut pas modifier le pointeur.

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

La variable *line* a le type de structure nommé *list*. Le type de structure *list* a trois membres : le premier membre est un pointeur vers une valeur **char**, le second est une valeur **int** et le troisième est un pointeur vers une autre structure *list*.

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

La variable *record* a le type de structure nommé *id*. Notez que *pname* est déclaré comme un pointeur vers un autre type de structure nommé *name*. Cette déclaration peut apparaître avant que le type *name* soit défini.

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)