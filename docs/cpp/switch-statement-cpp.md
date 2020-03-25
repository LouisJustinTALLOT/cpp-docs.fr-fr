---
title: switch, instruction (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160812"
---
# <a name="switch-statement-c"></a>switch, instruction (C++)

Autorise la sélection parmi plusieurs sections de code, selon la valeur d'une expression intégrale.

## <a name="syntax"></a>Syntaxe

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Notes

L' *expression* doit être d’un type intégral ou d’un type de classe pour lequel il existe une conversion non ambiguë en type intégral. La promotion intégrale est effectuée comme décrit dans [conversions standard](standard-conversions.md).

Le corps de l’instruction **switch** se compose d’une série d’étiquettes **case** et d’une étiquette **par défaut** facultative. Deux expressions constantes dans les instructions **case** ne peuvent pas avoir la même valeur. L’étiquette **par défaut** ne peut apparaître qu’une seule fois. Les instructions étiquetées ne sont pas des exigences syntaxiques, mais l’instruction **switch** est sans signification.   L'instruction par défaut n'a pas besoin d'être à la fin ; elle peut apparaître n'importe où dans le corps de l'instruction switch. Une étiquette case ou default ne peut apparaître que dans une instruction switch.

L' *expression constante* dans chaque étiquette **case** est convertie vers le type d' *expression* et comparée à l' *expression* pour l’égalité. Le contrôle passe à l’instruction dont **case** *constant-expression* correspond à la valeur de l' *expression*. Le comportement résultant est indiqué dans le tableau suivant.

### <a name="switch-statement-behavior"></a>Comportement de l'instruction switch

|Condition|Action|
|---------------|------------|
|La valeur convertie correspond à celle de l'expression de contrôle promue.|Le contrôle est transféré à l'instruction qui suit cette étiquette.|
|Aucune des constantes ne correspond aux constantes des étiquettes **case** ; une étiquette **par défaut** est présente.|Le contrôle est transféré à l’étiquette **par défaut** .|
|Aucune des constantes ne correspond aux constantes des étiquettes **case** ; l’étiquette **par défaut** n’est pas présente.|Le contrôle est transféré à l’instruction après l’instruction **switch** .|

Si une expression correspondante est trouvée, le contrôle n’est pas entravé par le **cas** suivant ou par les étiquettes **par défaut** . L’instruction [break](../cpp/break-statement-cpp.md) est utilisée pour arrêter l’exécution et transférer le contrôle à l’instruction après l’instruction **switch** . Sans instruction **break** , chaque instruction de l’étiquette **case** correspondante à la fin du **commutateur**, y compris la **valeur par défaut**, est exécutée. Par exemple :

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

Dans l'exemple ci-dessus, `capa` est incrémenté si `c` est un `A` majuscule. L’instruction **break** après `capa++` termine l’exécution du corps de l’instruction **switch** et le contrôle passe à la boucle **while** . Sans l’instruction **break** , l’exécution passe à l’instruction étiquetée suivante, afin que `lettera` et `nota` soient également incrémentés. Un objectif similaire est pris en charge par l’instruction **break** pour `case 'a'`. Si `c` est un `a`en minuscules, `lettera` est incrémenté et l’instruction **break** termine le corps de l’instruction **switch** . Si `c` n’est pas un `a` ou `A`, l’instruction **par défaut** est exécutée.

**Visual Studio 2017 et versions ultérieures :** (disponible avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) l’attribut `[[fallthrough]]` est spécifié dans la norme c++ 17. Il peut être utilisé dans une instruction **switch** comme indicateur pour le compilateur (ou pour toute personne lisant le code) qui est prévu. Actuellement, C++ le compilateur Microsoft n’émet pas d’avertissement sur le comportement FallThrough. cet attribut n’a donc aucun effet sur le comportement du compilateur. Notez que l’attribut est appliqué à une instruction vide au sein de l’instruction étiquetée ; en d’autres termes, le point-virgule est nécessaire.

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

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : une instruction switch peut introduire et initialiser une variable dont la portée est limitée au bloc de l’instruction switch :

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

Un bloc interne d’une instruction **switch** peut contenir des définitions avec des initialisations tant qu’elles sont accessibles, c’est-à-dire qu’elles ne sont pas ignorées par tous les chemins d’exécution possibles. Les noms présentés à l'aide de ces déclarations ont une portée locale. Par exemple :

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

Une instruction **switch** peut être imbriquée. Dans ce cas, les étiquettes **case** ou **default** s’associent à l’instruction **switch** la plus proche qui les englobe.

**Section spécifique de Microsoft**

Microsoft C ne limite pas le nombre de valeurs case dans une instruction **switch** . Le nombre est limité uniquement par la mémoire disponible. La norme C ANSI requiert au moins 257 étiquettes de cas sont autorisées dans une instruction **switch** .

Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) pour désactiver ces extensions.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
