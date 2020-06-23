---
title: return, instruction (C)
description: L’instruction return du langage C met fin à l’exécution de la fonction et retourne éventuellement une valeur à l’appelant.
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716292"
---
# <a name="return-statement-c"></a>return, instruction (C)

Une **`return`** instruction met fin à l’exécution d’une fonction et retourne le contrôle à la fonction appelante. L'exécution reprend dans la fonction d'appel au point immédiatement après l'appel. Une **`return`** instruction peut retourner une valeur à la fonction appelante. Pour plus d’informations, consultez [type de retour](../c-language/return-type.md).

## <a name="syntax"></a>Syntax

> *instruction Jump*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**`return`***expression*&#8203;<sub>OPT</sub>**`;`**

La valeur de l’*expression*, si celle-ci est présente, est retournée à la fonction appelante. Si l’*expression* est omise, la valeur de retour de la fonction n’est pas définie. L’expression, si elle est présente, est évaluée, puis convertie dans le type retourné par la fonction. Lorsqu’une **`return`** instruction contient une expression dans des fonctions qui ont un **`void`** type de retour, le compilateur génère un avertissement et l’expression n’est pas évaluée.

Si aucune **`return`** instruction ne s’affiche dans une définition de fonction, le contrôle retourne automatiquement à la fonction appelante après l’exécution de la dernière instruction de la fonction appelée. Dans ce cas, la valeur de retour de la fonction appelée est indéfinie. Si la fonction a un type de retour autre que **`void`** , il s’agit d’un bogue sérieux et le compilateur imprime un message de diagnostic d’avertissement. Si la fonction a un **`void`** type de retour, ce comportement est correct, mais peut être considéré comme un style médiocre. Utilisez une **`return`** instruction simple pour clarifier votre intention.

Une bonne pratique d’ingénierie consiste à toujours spécifier un type de retour pour vos fonctions. Si aucune valeur de retour n’est requise, déclarez la fonction pour qu’elle ait le **`void`** type de retour. Si un type de retour n’est pas spécifié, le compilateur C utilise un type de retour par défaut de **`int`** .

De nombreux programmeurs utilisent des parenthèses pour encadrer l’argument *expression* de l' **`return`** instruction. Toutefois, C ne requiert pas les parenthèses.

Le compilateur peut émettre un message d’avertissement de diagnostic sur du code inaccessible s’il trouve des instructions placées après l' **`return`** instruction.

Dans une **`main`** fonction, l' **`return`** instruction et l’expression sont facultatives. Ce qui arrive à la valeur retournée, si elle est spécifiée, dépend de l’implémentation. **Spécifique à Microsoft**: l’implémentation Microsoft C retourne la valeur d’expression au processus qui a appelé le programme, tel que *`cmd.exe`* . Si aucune **`return`** expression n’est fournie, le runtime C de Microsoft retourne une valeur qui indique la réussite (0) ou l’échec (une valeur différente de zéro).

## <a name="example"></a>Exemple

Cet exemple est un programme en plusieurs parties. Il illustre l' **`return`** instruction, et comment il est utilisé à la fois pour terminer l’exécution de la fonction et éventuellement pour retourner une valeur.

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

La `square` fonction retourne le carré de son argument, dans un type plus étendu pour empêcher une erreur arithmétique. **Spécifique à Microsoft**: dans l’implémentation Microsoft C, le **`long long`** type est suffisamment grand pour contenir le produit de deux **`int`** valeurs sans dépassement de capacité.

Les parenthèses autour de l' **`return`** expression dans `square` sont évaluées dans le cadre de l’expression et ne sont pas requises par l' **`return`** instruction.

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

La `ratio` fonction retourne le rapport de ses deux **`int`** arguments sous la forme d’une valeur à virgule flottante **`double`** . L' **`return`** expression est forcée d’utiliser une opération à virgule flottante en effectuant un cast de l’un des opérandes en **`double`** . Dans le cas contraire, l’opérateur de division entière est utilisé et la partie fractionnaire est perdue.

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

La `report_square` fonction appelle `square` avec une valeur de paramètre de `INT_MAX` , la plus grande valeur entière signée qui s’ajuste à un **`int`** . Le **`long long`** résultat est stocké dans `squared` , puis imprimé. La `report_square` fonction a un **`void`** type de retour, donc elle n’a pas d’expression dans son **`return`** instruction.

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

La `report_ratio` fonction appelle `ratio` avec les valeurs de paramètres de `1` et `INT_MAX` . Le **`double`** résultat est stocké dans `fraction` , puis imprimé. La `report_ratio` fonction a un **`void`** type de retour, donc il n’est pas nécessaire de retourner explicitement une valeur. L’exécution de `report_ratio` « sort du bas » et ne retourne aucune valeur à l’appelant.

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

La **`main`** fonction appelle deux fonctions : `report_square` et `report_ratio` . Comme `report_square` ne prend pas de paramètres et retourne **`void`** , nous n’assignons pas son résultat à une variable. De même, `report_ratio` retourne **`void`** , donc nous n’enregistrons pas sa valeur de retour. Après chacun de ces appels de fonction, l’exécution se poursuit à l’instruction suivante. **`main`** Retourne ensuite `0` la valeur (généralement utilisée pour signaler la réussite) pour mettre fin au programme.

Pour compiler l’exemple, créez un fichier de code source nommé *`C_return_statement.c`* . Copiez ensuite tout l’exemple de code, dans l’ordre indiqué. Enregistrez le fichier et compilez-le dans une fenêtre d’invite de commandes développeur à l’aide de la commande :

**`cl /W4 C_return_statement.c`**

Ensuite, pour exécuter l’exemple de code, entrez **`C_return_statement.exe`** à l’invite de commandes. La sortie de l’exemple ressemble à ceci :

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>Voir aussi

[Publication](../c-language/statements-c.md)
