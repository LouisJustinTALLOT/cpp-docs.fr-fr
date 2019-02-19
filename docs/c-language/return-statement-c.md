---
title: return, instruction (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148983"
---
# <a name="return-statement-c"></a>return, instruction (C)

L’instruction `return` termine l’exécution d’une fonction et retourne le contrôle à la fonction appelante. L'exécution reprend dans la fonction d'appel au point immédiatement après l'appel. Une instruction `return` peut également retourner une valeur à la fonction appelante. Pour plus d’informations, consultez [Type de retour](../c-language/return-type.md).

## <a name="syntax"></a>Syntaxe

*saut-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

La valeur de l’*expression*, si celle-ci est présente, est retournée à la fonction appelante. Si l’*expression* est omise, la valeur de retour de la fonction n’est pas définie. L’expression, si elle est présente, est évaluée, puis convertie dans le type retourné par la fonction. Si la fonction a été déclarée avec un type de retour `void`, une instruction `return` contenant une expression génère un avertissement et l’expression n’est pas évaluée.

Si aucune instruction `return` n’apparaît dans une définition de fonction, le contrôle retourne automatiquement à la fonction appelante après l’exécution de la dernière instruction de la fonction appelée. Dans ce cas, la valeur de retour de la fonction appelée est indéfinie. Si une valeur de retour n’est pas obligatoire, déclarez la fonction comme devant avoir le type de retour `void` ; sinon, le type de retour par défaut est `int`.

De nombreux programmeurs utilisent des parenthèses pour encadrer l’argument *expression* de l’instruction `return`. Toutefois, C ne nécessite pas de parenthèses.

Cet exemple illustre l'instruction `return` :

```C
#include <limits.h>
#include <stdio.h>

void draw( int i, long long ll );
long long sq( int s );

int main()
{
    long long y;
    int x = INT_MAX;

    y = sq( x );
    draw( x, y );
    return x;
}

long long sq( int s )
{
    // Note that parentheses around the return expression
    // are allowed but not required here.
    return( s * (long long)s );
}

void draw( int i, long long ll )
{
    printf( "i = %d, ll = %lld\n", i, ll );
    return;
}
```

Dans cet exemple, la fonction `main` appelle deux fonctions : `sq` et `draw`. La fonction `sq` retourne la valeur de `x * x` à `main`, où la valeur de retour est assignée à `y`. Les parenthèses autour de l’expression de retour dans `sq` sont évaluées dans le cadre de l’expression et ne sont pas exigées par l’instruction return. Étant donné que l’expression de retour est évaluée avant d’être convertie en type de retour, `sq` force le type d’expression à être le type de retour avec un cast pour éviter un dépassement éventuel sur les entiers, ce qui pourrait produire des résultats inattendus. La fonction `draw` est déclarée en tant que fonction `void`. Elle affiche les valeurs de ses paramètres, puis l’instruction return vide met fin à la fonction et ne retourne pas de valeur. Une tentative d’assigner la valeur de retour de `draw` entraînerait l’émission d’un message de diagnostic. Ensuite, la fonction `main` retourne la valeur de `x` au système d’exploitation.

La sortie de l’exemple ressemble à ceci :

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
