---
description: 'En savoir plus sur : type de retour'
title: Type de retour
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 5f4c3c59dd5d89a3c9083eb177bb72e4049ab454
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293025"
---
# <a name="return-type"></a>Type de retour

Le type de retour d’une fonction génère la taille et le type de la valeur retournée par la fonction et correspond au spécificateur de type dans la syntaxe ci-dessous :

## <a name="syntax"></a>Syntaxe

*définition de fonction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**attribute-SEQ* est spécifique à Microsoft\*/

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*type-specifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`void`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`char`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`short`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`int`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int8`** /\* Spécifique à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int16`** /\* Spécifique à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int32`** /\* Spécifique à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__int64`** /\* Spécifique à Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`long`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`float`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`double`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`signed`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`unsigned`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-Union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*type-specifier* peut spécifier tout type fondamental, structure ou union. Si vous n’incluez pas *type-specifier*, le type de retour **`int`** est supposé.

Le type de retour donné dans la définition de fonction doit correspondre au type de retour dans les déclarations de la fonction ailleurs dans le programme. Une fonction retourne une valeur lorsqu’une **`return`** instruction contenant une expression est exécutée. L'expression est évaluée, si nécessaire convertie vers le type de valeur de retour et retournée au point auquel la fonction a été appelée. Si une fonction est déclarée avec le type de retour **`void`** , une instruction return contenant une expression génère un avertissement et l’expression n’est pas évaluée.

Les exemples suivants illustrent des valeurs de retour de fonction.

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

Cet exemple définit le `STUDENT` type avec une **`typedef`** déclaration et définit la fonction `sortstu` pour avoir un `STUDENT` type de retour. La fonction sélectionne et retourne un de ses arguments de structure. Dans les appels suivants à la fonction, le compilateur effectue une vérification pour s'assurer que les types d'argument sont `STUDENT`.

> [!NOTE]
> L'efficacité est améliorée en passant des pointeurs à la structure plutôt qu'à la structure entière.

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

Cet exemple définit une fonction qui retourne un pointeur vers un tableau de caractères. La fonction accepte deux tableaux de caractères (chaînes) comme arguments et retourne un pointeur vers la plus courte des deux chaînes. Un pointeur vers un tableau pointe vers le premier des éléments du tableau et a son type ; par conséquent, le type de retour de la fonction est un pointeur vers le type **`char`** .

Vous n’avez pas besoin de déclarer des fonctions avec le **`int`** type de retour avant de les appeler, bien que les prototypes soient recommandés afin que la vérification de type correcte pour les arguments et les valeurs de retour soit activée.

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
