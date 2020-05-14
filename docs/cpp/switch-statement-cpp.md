---
title: switchinstruction (C++)
description: Référence à l’instruction C++ standard switch dans Microsoft Visual Studio c++.
ms.date: 04/25/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83389699"
---
# <a name="switch-statement-c"></a>`switch`instruction (C++)

Autorise la sélection parmi plusieurs sections de code, selon la valeur d'une expression intégrale.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Notes

Une __`switch`__ instruction provoque le transfert du contrôle à un *`labeled-statement`* dans son corps d’instruction, en fonction de la valeur de *`condition`* .

Le *`condition`* doit avoir un type intégral ou être un type de classe qui a une conversion non ambiguë en type intégral. La promotion intégrale a lieu comme décrit dans [conversions standard](standard-conversions.md).

Le __`switch`__ corps de l’instruction se compose d’une série d' __`case`__ étiquettes et d’une __`default`__ étiquette facultative. Un *`labeled-statement`* est l’une de ces étiquettes et les instructions qui suivent. Les instructions étiquetées ne sont pas des exigences syntaxiques, mais l' __`switch`__ instruction n’a aucune signification. *`constant-expression`* __`case`__ Les instructions ne peuvent pas avoir la même valeur pour deux valeurs. L' __`default`__ étiquette ne peut apparaître qu’une seule fois. L' __`default`__ instruction est souvent placée à la fin, mais elle peut apparaître n’importe où dans le corps de l' __`switch`__ instruction. Une __`case`__ __`default`__ étiquette ou ne peut apparaître qu’à l’intérieur d’une __`switch`__ instruction.

Le *`constant-expression`* de chaque __`case`__ étiquette est converti en une valeur constante qui est du même type que *`condition`* . Ensuite, il est comparé à *`condition`* pour l’égalité. Le contrôle passe à la première instruction après la __`case`__ *`constant-expression`* valeur qui correspond à la valeur de *`condition`* . Le comportement résultant est indiqué dans le tableau suivant.

### <a name="switch-statement-behavior"></a>`switch`comportement des instructions

| Condition | Action |
|--|--|
| La valeur convertie correspond à celle de l'expression de contrôle promue. | Le contrôle est transféré à l'instruction qui suit cette étiquette. |
| Aucune des constantes ne correspond aux constantes des __`case`__ étiquettes ; une __`default`__ étiquette est présente. | Le contrôle est transféré vers l' __`default`__ étiquette. |
| Aucune des constantes ne correspond aux constantes des __`case`__ étiquettes ; aucune __`default`__ étiquette n’est présente. | Le contrôle est transféré à l’instruction après l' __`switch`__ instruction. |

Si une expression correspondante est trouvée, l’exécution peut passer par la suite __`case`__ ou les __`default`__ étiquettes. L' [`break`](../cpp/break-statement-cpp.md) instruction est utilisée pour arrêter l’exécution et transférer le contrôle à l’instruction après l' __`switch`__ instruction. Sans __`break`__ instruction, chaque instruction de l' __`case`__ étiquette mise en correspondance à la fin de __`switch`__ , y compris le __`default`__ , est exécutée. Par exemple :

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

Dans l'exemple ci-dessus, `uppercase_A` est incrémenté si `c` est un `'A'` majuscule. L' __`break`__ instruction après `uppercase_A++` termine l’exécution du __`switch`__ corps de l’instruction et le contrôle passe à la __`while`__ boucle. Sans l' __`break`__ instruction, l’exécution passe à l’instruction étiquetée suivante, afin que `lowercase_a` et `other` soient également incrémentés. Un objectif similaire est pris en charge par l' __`break`__ instruction pour `case 'a'` . Si `c` est un `'a'` en minuscule, `lowercase_a` est incrémenté et l' __`break`__ instruction termine le corps de l' __`switch`__ instruction. Si `c` n’est pas `'a'` ou `'A'` , __`default`__ l’instruction est exécutée.

**Visual Studio 2017 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) l' `[[fallthrough]]` attribut est spécifié dans la norme c++ 17. Vous pouvez l’utiliser dans une __`switch`__ instruction. C’est un indice pour le compilateur, ou quiconque lit le code, ce comportement de passage est intentionnel. Actuellement, le compilateur Microsoft C++ n’émet pas d’avertissement sur le comportement FallThrough. cet attribut n’a donc aucun effet sur le comportement du compilateur. Dans l’exemple, l’attribut est appliqué à une instruction vide au sein de l’instruction étiquetée non terminée. En d’autres termes, le point-virgule est nécessaire.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)). Une __`switch`__ instruction peut avoir une *`init-statement`* clause, qui se termine par un point-virgule. Il introduit et Initialise une variable dont la portée est limitée au bloc de l' __`switch`__ instruction :

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

Un bloc interne d’une __`switch`__ instruction peut contenir des définitions avec des initialiseurs à condition qu’ils soient *accessibles*, c’est-à-dire qu’ils ne sont pas ignorés par tous les chemins d’exécution possibles. Les noms présentés à l'aide de ces déclarations ont une portée locale. Par exemple :

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

Une __`switch`__ instruction peut être imbriquée. Lorsqu’ils sont imbriqués, les __`case`__ étiquettes ou s' __`default`__ associent à l’instruction la plus proche __`switch`__ qui les englobe.

### <a name="microsoft-specific-behavior"></a>Comportement spécifique à Microsoft

Microsoft C++ ne limite pas le nombre de __`case`__ valeurs dans une __`switch`__ instruction. Le nombre est limité uniquement par la mémoire disponible.

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
