---
title: switch, instruction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32fcf4f8f99f80e44758c107a8941c51bd8a767f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821164"
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

Le *expression* doit être de type intégral ou d’un type de classe pour laquelle il existe une conversion non ambiguë en type intégral. Promotion intégrale est exécutée comme décrit dans [Conversions Standard](standard-conversions.md).

Le **basculer** corps d’instruction se compose d’une série de **cas** étiquettes et éventuellement un **par défaut** étiquette. Aucun deux expressions de constante dans **cas** instructions peuvent correspondre à la même valeur. Le **par défaut** étiquette peut apparaître qu’une seule fois. Les instructions étiquetées ne sont pas des exigences syntaxiques, mais la **basculer** instruction n’a aucune signification sans eux.   L'instruction par défaut n'a pas besoin d'être à la fin ; elle peut apparaître n'importe où dans le corps de l'instruction switch. Une étiquette case ou default ne peut apparaître que dans une instruction switch.

Le *expression constante* dans chaque **cas** est converti vers le type de *expression* et comparé *expression* pour égalité. Le contrôle passe à l’instruction dont **cas** *expression constante* correspond à la valeur de *expression*. Le comportement résultant est indiqué dans le tableau suivant.

### <a name="switch-statement-behavior"></a>Comportement de l'instruction switch

|Condition|Action|
|---------------|------------|
|La valeur convertie correspond à celle de l'expression de contrôle promue.|Le contrôle est transféré à l'instruction qui suit cette étiquette.|
|Aucun des constantes ne correspond à l’une des constantes dans le **cas** étiquettes ; un **par défaut** étiquette n’est présente.|Le contrôle est transféré à la **par défaut** étiquette.|
|Aucun des constantes ne correspond à l’une des constantes dans le **cas** étiquettes ; **par défaut** étiquette n’est pas présente.|Le contrôle est transféré à l’instruction après le **basculer** instruction.|

Si une expression correspondante est trouvée, le contrôle n’est pas bloqué par les **cas** ou **par défaut** étiquettes. Le [saut](../cpp/break-statement-cpp.md) instruction est utilisée pour arrêter l’exécution et de transférer le contrôle à l’instruction après le **basculer** instruction. Sans un **saut** chaque instruction, à partir de la mise en correspondance **cas** étiquette à la fin de la **basculer**, y compris le **par défaut**, est exécutée. Exemple :

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

Dans l'exemple ci-dessus, `capa` est incrémenté si `c` est un `A` majuscule. Le **saut** instruction après `capa++` termine l’exécution de la **basculer** corps d’instruction et le contrôle passe à la **tandis que** boucle. Sans le **saut** instruction, l’exécution serait « passer » à l’instruction étiquetée suivante, afin que `lettera` et `nota` seraient également incrémentés. Un objectif similaire est pris en charge par le **saut** instruction pour `case 'a'`. Si `c` est une minuscule `a`, `lettera` est incrémentée et le **saut** instruction met fin à la **basculer** corps de l’instruction. Si `c` n’est pas un `a` ou `A`, le **par défaut** instruction est exécutée.

**Visual Studio 2017 et versions ultérieur :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) le `[[fallthrough]]` attribut est spécifié dans la norme C ++ 17. Il peut être utilisé dans un **basculer** instruction en tant qu’indicateur du compilateur (ou à toute personne lisant le code) ce comportement FallThrough est prévu. Le compilateur Visual C++ n’avertit actuellement pas sur le comportement fallthrough, cet attribut n’a aucun effet sur le comportement du compilateur. Notez que l’attribut est appliqué à une instruction vide au sein de l’instruction étiquetée ; en d’autres termes, le point-virgule est nécessaire.

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

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : une instruction switch peut introduire et initialiser une variable dont la portée est limitée au bloc de l’instruction switch :

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

Un bloc interne d’un **basculer** instruction peut contenir des définitions avec des initialisations tant qu’ils sont accessibles, c'est-à-dire non contournées par tous les chemins d’exécution possibles. Les noms présentés à l'aide de ces déclarations ont une portée locale. Exemple :

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

Un **basculer** instruction peut être imbriquée. Dans ce cas, **cas** ou **par défaut** étiquettes associer la plus proche **basculer** instruction qui les entoure.

**Section spécifique à Microsoft**

Microsoft C ne limite pas le nombre de valeurs de cas dans un **basculer** instruction. Le nombre est limité uniquement par la mémoire disponible. C ANSI requiert qu’au moins 257 étiquettes soient autorisées dans un **basculer** instruction.

Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez le [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur pour désactiver ces extensions.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)