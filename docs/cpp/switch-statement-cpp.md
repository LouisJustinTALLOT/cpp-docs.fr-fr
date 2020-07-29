---
title: :::no-loc(switch):::instruction (C++)
description: 'Référence à l’instruction C++ standard :::no-loc(switch)::: dans Microsoft Visual Studio c++.'
ms.date: 04/25/2020
f1_keywords:
- :::no-loc(default):::_cpp
- :::no-loc(switch):::_cpp
- :::no-loc(case):::_cpp
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C++]'
- ':::no-loc(case)::: keyword [C++], in :::no-loc(switch)::: statements'
- ':::no-loc(default)::: keyword [C++]'
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
- ':::no-loc(while):::'
- ':::no-loc(opt):::'
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d71989b6d8af0213c4cd6d4fbd8d5a84b318701a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223588"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`instruction (C++)

Autorise la sélection parmi plusieurs sections de code, selon la valeur d'une expression intégrale.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;**`:::no-loc(switch):::`**&nbsp;**`(`**&nbsp;*`init-statement`*<sub>:::no-loc(opt):::</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;**`)`**&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>:::no-loc(opt):::</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Notes

Une **`:::no-loc(switch):::`** instruction provoque le transfert du contrôle à un *`labeled-statement`* dans son corps d’instruction, en fonction de la valeur de *`condition`* .

Le *`condition`* doit avoir un type intégral ou être un type de classe qui a une conversion non ambiguë en type intégral. La promotion intégrale a lieu comme décrit dans [conversions standard](standard-conversions.md).

Le **`:::no-loc(switch):::`** corps de l’instruction se compose d’une série d' **`:::no-loc(case):::`** étiquettes et d’une :::no-loc(opt)::: **`:::no-loc(default):::`** étiquette ional. Un *`labeled-statement`* est l’une de ces étiquettes et les instructions qui suivent. Les instructions étiquetées ne sont pas des exigences syntaxiques, mais l' **`:::no-loc(switch):::`** instruction n’a aucune signification. *`constant-expression`* **`:::no-loc(case):::`** Les instructions ne peuvent pas avoir la même valeur pour deux valeurs. L' **`:::no-loc(default):::`** étiquette ne peut apparaître qu’une seule fois. L' **`:::no-loc(default):::`** instruction est souvent placée à la fin, mais elle peut apparaître n’importe où dans le corps de l' **`:::no-loc(switch):::`** instruction. Une **`:::no-loc(case):::`** **`:::no-loc(default):::`** étiquette ou ne peut apparaître qu’à l’intérieur d’une **`:::no-loc(switch):::`** instruction.

Le *`constant-expression`* de chaque **`:::no-loc(case):::`** étiquette est converti en une valeur constante qui est du même type que *`condition`* . Ensuite, il est comparé à *`condition`* pour l’égalité. Le contrôle passe à la première instruction après la **`:::no-loc(case):::`** *`constant-expression`* valeur qui correspond à la valeur de *`condition`* . Le comportement résultant est indiqué dans le tableau suivant.

### <a name="no-locswitch-statement-behavior"></a>`:::no-loc(switch):::`comportement des instructions

| Condition | Action |
|--|--|
| La valeur convertie correspond à celle de l'expression de contrôle promue. | Le contrôle est transféré à l'instruction qui suit cette étiquette. |
| Aucune des constantes ne correspond aux constantes des **`:::no-loc(case):::`** étiquettes ; une **`:::no-loc(default):::`** étiquette est présente. | Le contrôle est transféré vers l' **`:::no-loc(default):::`** étiquette. |
| Aucune des constantes ne correspond aux constantes des **`:::no-loc(case):::`** étiquettes ; aucune **`:::no-loc(default):::`** étiquette n’est présente. | Le contrôle est transféré à l’instruction après l' **`:::no-loc(switch):::`** instruction. |

Si une expression correspondante est trouvée, l’exécution peut passer par la suite **`:::no-loc(case):::`** ou les **`:::no-loc(default):::`** étiquettes. L' [`:::no-loc(break):::`](../cpp/:::no-loc(break):::-statement-cpp.md) instruction est utilisée pour arrêter l’exécution et transférer le contrôle à l’instruction après l' **`:::no-loc(switch):::`** instruction. Sans **`:::no-loc(break):::`** instruction, chaque instruction de l' **`:::no-loc(case):::`** étiquette mise en correspondance à la fin de **`:::no-loc(switch):::`** , y compris le **`:::no-loc(default):::`** , est exécutée. Par exemple :

```cpp
// :::no-loc(switch):::_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, other;
   char c;
   upper:::no-loc(case):::_A = lower:::no-loc(case):::_a = other = 0;

   :::no-loc(while)::: ( c = *buffer++ )   // Walks buffer until NULL
   {
      :::no-loc(switch)::: ( c )
      {
         :::no-loc(case)::: 'A':
            upper:::no-loc(case):::_A++;
            :::no-loc(break):::;
         :::no-loc(case)::: 'a':
            lower:::no-loc(case):::_a++;
            :::no-loc(break):::;
         :::no-loc(default)::::
            other++;
      }
   }
   printf_s( "\nUpper:::no-loc(case)::: A: %d\nLower:::no-loc(case)::: a: %d\nTotal: %d\n",
      upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, (upper:::no-loc(case):::_A + lower:::no-loc(case):::_a + other) );
}
```

Dans l’exemple ci-dessus, `upper:::no-loc(case):::_A` est incrémenté si `c` est un supérieur :::no-loc(case)::: `'A'` . L' **`:::no-loc(break):::`** instruction après `upper:::no-loc(case):::_A++` termine l’exécution du **`:::no-loc(switch):::`** corps de l’instruction et le contrôle passe à la **`:::no-loc(while):::`** boucle. Sans l' **`:::no-loc(break):::`** instruction, l’exécution passe à l’instruction étiquetée suivante, afin que `lower:::no-loc(case):::_a` et `other` soient également incrémentés. Un objectif similaire est pris en charge par l' **`:::no-loc(break):::`** instruction pour `:::no-loc(case)::: 'a'` . Si `c` est un inférieur :::no-loc(case)::: `'a'` , `lower:::no-loc(case):::_a` est incrémenté et l' **`:::no-loc(break):::`** instruction termine le **`:::no-loc(switch):::`** corps de l’instruction. Si `c` n’est pas `'a'` ou `'A'` , **`:::no-loc(default):::`** l’instruction est exécutée.

**Visual Studio 2017 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) l' `[[fallthrough]]` attribut est spécifié dans la norme c++ 17. Vous pouvez l’utiliser dans une **`:::no-loc(switch):::`** instruction. C’est un indice pour le compilateur, ou quiconque lit le code, ce comportement de passage est intentionnel. Actuellement, le compilateur Microsoft C++ n’émet pas d’avertissement sur le comportement FallThrough. cet attribut n’a donc aucun effet sur le comportement du compilateur. Dans l’exemple, l’attribut est appliqué à une instruction vide au sein de l’instruction étiquetée non terminée. En d’autres termes, le point-virgule est nécessaire.

```cpp
int main()
{
    int n = 5;
    :::no-loc(switch)::: (n)
    {

    :::no-loc(case)::: 1:
        a();
        :::no-loc(break):::;
    :::no-loc(case)::: 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    :::no-loc(case)::: 3:
        c();
        :::no-loc(break):::;
    :::no-loc(default)::::
        d();
        :::no-loc(break):::;
    }

    return 0;
}
```

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)). Une **`:::no-loc(switch):::`** instruction peut avoir une *`init-statement`* clause, qui se termine par un point-virgule. Il introduit et Initialise une variable dont la portée est limitée au bloc de l' **`:::no-loc(switch):::`** instruction :

```cpp
    :::no-loc(switch)::: (Gadget gadget(args); auto s = gadget.get_status())
    {
    :::no-loc(case)::: status::good:
        gadget.zip();
        :::no-loc(break):::;
    :::no-loc(case)::: status::bad:
        throw BadGadget();
    };
```

Un bloc interne d’une **`:::no-loc(switch):::`** instruction peut contenir des définitions avec des initialiseurs à condition qu’ils soient *accessibles*, c’est-à-dire qu’ils ne sont pas ignorés par tous les chemins d’exécution possibles. Les noms présentés à l'aide de ces déclarations ont une portée locale. Par exemple :

```cpp
// :::no-loc(switch):::_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    :::no-loc(switch):::( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    :::no-loc(case)::: 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        :::no-loc(break):::;

    :::no-loc(case)::: 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        :::no-loc(break):::;

    :::no-loc(default)::::
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        :::no-loc(break):::;
    }
}
```

Une **`:::no-loc(switch):::`** instruction peut être imbriquée. Lorsqu’ils sont imbriqués, les **`:::no-loc(case):::`** étiquettes ou s' **`:::no-loc(default):::`** associent à l’instruction la plus proche **`:::no-loc(switch):::`** qui les englobe.

### <a name="microsoft-specific-behavior"></a>Comportement spécifique à Microsoft

Microsoft C++ ne limite pas le nombre de **`:::no-loc(case):::`** valeurs dans une **`:::no-loc(switch):::`** instruction. Le nombre est limité uniquement par la mémoire disponible.

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
