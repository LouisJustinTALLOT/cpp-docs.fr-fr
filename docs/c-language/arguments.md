---
title: Arguments
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e1c88034044c74a542384873454f993b6bce3244
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232662"
---
# <a name="arguments"></a>Arguments

Les arguments figurant dans un appel de fonction ont la forme suivante :

> *expression* **(** *expression-List*<SUB>OPT</SUB> **)** /* appel de fonction */

Dans un appel de fonction, *expression-list* est une liste d'expressions (séparées par des virgules). Les valeurs de ces dernières expressions sont les arguments passés à la fonction. Si la fonction n’accepte aucun argument, *expression-List* doit contenir le mot clé **`void`** .

Un argument peut être une valeur quelconque dotée du type fondamental, structure, union ou pointeur. Tous les arguments sont passés par valeur. Cela signifie qu'une copie de l'argument est assignée au paramètre correspondant. La fonction ne connaît pas l'emplacement mémoire réel de l'argument passé. La fonction utilise cette copie sans affecter la variable de laquelle elle était initialement dérivée.

Vous ne pouvez pas passer des tableaux ni des fonctions en tant qu'arguments, mais vous pouvez passer des pointeurs désignant ces éléments. Les pointeurs fournissent un moyen à une fonction d'accéder à une valeur par référence. Comme un pointeur vers une variable contient l'adresse de la variable, la fonction peut utiliser cette adresse pour accéder à la valeur de la variable. Les arguments de pointeur permettent à une fonction d'accéder aux tableaux et aux fonctions, même si les tableaux et les fonctions ne peuvent pas être passés en tant qu'arguments.

L'ordre dans lequel les arguments sont évalués peut varier selon les différents compilateurs et niveaux d'optimisation. Toutefois, les arguments et tous les effets secondaires sont complètement évalués avant que la fonction soit entrée. Consultez [Effets secondaires](../c-language/side-effects.md) pour obtenir des informations sur les effets secondaires.

L’argument *expression-list* dans un appel de fonction est évalué et les conversions arithmétiques habituelles sont effectuées sur chaque argument dans l’appel de fonction. Si un prototype est disponible, le type d’argument résultant est comparé au paramètre correspondant du prototype. S'ils ne correspondent pas, une conversion est exécutée ou un message de diagnostic est publié. Les paramètres subissent également les conversions arithmétiques habituelles.

Le nombre d’expressions dans *expression-list* doit correspondre au nombre de paramètres, à moins que le prototype ou la définition de la fonction spécifie explicitement un nombre variable d’arguments. Dans ce cas, le compilateur vérifie autant d’arguments qu’il existe de noms de types dans la liste des paramètres, et les convertit si nécessaire, comme décrit ci-dessus. Consultez [Appels avec un nombre variable d’arguments](../c-language/calls-with-a-variable-number-of-arguments.md) pour plus d’informations.

Si la liste de paramètres du prototype contient uniquement le mot clé **`void`** , le compilateur attend zéro argument dans l’appel de fonction et zéro paramètre dans la définition. Un message de diagnostic est publié si des arguments sont détectés.

## <a name="example"></a>Exemple

L'exemple ci-dessous utilise des pointeurs comme arguments :

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

Dans cet exemple, la `swap` fonction est déclarée dans `main` pour avoir deux arguments, représentés respectivement par les identificateurs `num1` et `num2` , qui sont tous deux des pointeurs vers des **`int`** valeurs. Les paramètres `num1` et `num2` dans la définition de style prototype sont également déclarés comme pointeurs vers des **`int`** valeurs de type.

Dans l'appel de fonction

```C
swap( &x, &y )
```

l'adresse de `x` est stockée dans `num1` et l'adresse de `y` est stockée dans `num2`. À présent, deux noms, ou « alias », existent pour le même emplacement. Les références à `*num1` et `*num2` dans `swap` sont effectivement des références à `x` et `y` dans `main`. Les assignations dans `swap` échangent en fait les contenus de `x` et `y`. Par conséquent, aucune **`return`** instruction n’est nécessaire.

Le compilateur effectue la vérification des types sur les arguments passés à `swap` car le prototype de `swap` inclut des types d'argument pour chaque paramètre. Les identificateurs placés entre les parenthèses du prototype et de la définition peuvent être identiques ou différents. L’essentiel est que les types des arguments correspondent à ceux des listes de paramètres, dans le prototype et la définition.

## <a name="see-also"></a>Voir aussi

[Appels de fonction](../c-language/function-calls.md)
