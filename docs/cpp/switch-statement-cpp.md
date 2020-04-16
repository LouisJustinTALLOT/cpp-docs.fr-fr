---
title: switchdéclaration (C)
description: Référence à la déclaration switch Standard CMD dans Microsoft Visual Studio C.
ms.date: 04/15/2020
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
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480822"
---
# <a name="opno-locswitch-statement-c"></a>switchdéclaration (C)

Autorise la sélection parmi plusieurs sections de code, selon la valeur d'une expression intégrale.

## <a name="syntax"></a>Syntaxe

> **`switch (`**\[ *initialisation* **`;`**] *expression***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***déclaration* *d’expression* **`:`** constante\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***déclaration*] \
> **`}`**

## <a name="remarks"></a>Notes

*L’expression* doit avoir un type intégral, ou être un type de classe qui a une conversion sans ambiguïté en type intégral. La promotion intégrale a lieu comme décrit dans [les conversions Standard](standard-conversions.md).

L’organe **switch** de déclaration **case** se compose **default** d’une série d’étiquettes et d’une étiquette facultative. Collectivement, les énoncés qui suivent les étiquettes sont appelés *énoncés étiquetés.* Les déclarations étiquetées ne sont pas **switch** des exigences syntaxes, mais l’énoncé n’a aucun sens sans eux. Aucune expression constante **case** dans les déclarations ne peut évaluer à la même valeur. L’étiquette **default** ne peut apparaître qu’une seule fois. La **default** déclaration est souvent placée à la fin, mais **switch** elle peut apparaître n’importe où dans le corps de la déclaration. A **case** **default** ou une étiquette **switch** ne peut apparaître qu’à l’intérieur d’une déclaration.

*L’expression constante* **case** dans chaque étiquette est convertie au type d’expression. *expression* Ensuite, c’est comparé à *l’expression* pour l’égalité. Le contrôle passe **case** à la déclaration dont *l’expression constante* correspond à la valeur de l’expression . *expression* Le comportement résultant est indiqué dans le tableau suivant.

### <a name="switch-statement-behavior"></a>Comportement de déclaration de commutateur

| Condition | Action |
|--|--|
| La valeur convertie correspond à celle de l'expression de contrôle promue. | Le contrôle est transféré à l'instruction qui suit cette étiquette. |
| Aucune des constantes ne correspond **case** aux constantes des étiquettes ; une **default** étiquette est présente. | Le contrôle est **default** transféré à l’étiquette. |
| Aucune des constantes ne correspond **case** aux constantes des étiquettes ; aucune **default** étiquette n’est présente. | Le contrôle est transféré **switch** à la déclaration après la déclaration. |

Si une expression correspondante est trouvée, **case** **default** l’exécution peut se poursuivre par le biais d’étiquettes ultérieures ou. La [`break`](../cpp/break-statement-cpp.md) déclaration est utilisée pour arrêter l’exécution **switch** et transférer le contrôle à la déclaration après la déclaration. Sans **break** déclaration, chaque déclaration **case** de l’étiquette **switch** appariée **default** à la fin de la , y compris le , est exécuté. Par exemple :

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

Dans l'exemple ci-dessus, `uppercase_A` est incrémenté si `c` est un `'A'` majuscule. La **break** déclaration `uppercase_A++` après la **switch** fin de l’exécution **while** de l’organe de déclaration et le contrôle passe à la boucle. Sans **break** la déclaration, l’exécution « passerait » à `lowercase_a` `other` la déclaration suivante étiquetée, de sorte que et serait également incrémentée. Un but similaire est **break** servi `case 'a'`par la déclaration pour . Si `c` est une `'a'` `lowercase_a` majuscule, est incrémenté et la **break** déclaration met fin à l’organe **switch** de déclaration. Si `c` n’est `'a'` `'A'`pas **default** un ou , la déclaration est exécutée.

**Visual Studio 2017 et plus tard :** (disponible avec [/std:c '17](../build/reference/std-specify-language-standard-version.md)) L’attribut `[[fallthrough]]` est spécifié dans la norme C 17. Vous pouvez l’utiliser dans une **switch** déclaration. C’est un indice pour le compilateur, ou toute personne qui lit le code, que le comportement de chute est intentionnelle. Le compilateur Microsoft CMD actuellement ne met pas en garde sur le comportement de chute, de sorte que cet attribut n’a aucun effet sur le comportement compilateur. Dans l’exemple, l’attribut est appliqué à une déclaration vide dans la déclaration non déterminée étiquetée. En d’autres termes, le point-virgule est nécessaire.

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

**Visual Studio 2017 version 15.3 et plus tard** (disponible avec [/std:c '17](../build/reference/std-specify-language-standard-version.md)). Une switch déclaration peut avoir une clause *d’initialisation.* Il introduit et initialise une variable dont la portée switch est limitée au bloc de la déclaration :

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

Un bloc intérieur **switch** d’une déclaration peut contenir des définitions avec des initialisations aussi longtemps qu’elles sont accessibles, c’est-à-dire non contournées par tous les chemins d’exécution possibles. *reachable* Les noms présentés à l'aide de ces déclarations ont une portée locale. Par exemple :

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

Une **switch** déclaration peut être imbriquée. Lorsqu’ils sont **case** **default** imbriqués, **switch** les étiquettes ou les étiquettes s’associent à l’énoncé le plus proche qui les entoure.

### <a name="microsoft-specific-behavior"></a>Comportement spécifique à Microsoft

Microsoft C ne limite pas **case** le **switch** nombre de valeurs dans un communiqué. Le nombre est limité uniquement par la mémoire disponible. ANSI C exige qu’au **case** moins 257 étiquettes soient autorisées dans un **switch** communiqué.

Le default pour Microsoft C est que les extensions Microsoft sont activées. Utilisez l’option [compilateur /Za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots-clés](../cpp/keywords-cpp.md)
