---
title: /Zc:implicitNoexcept (spécificateurs d'exceptions implicites)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: bb1a632ffe684ac0777d0089a2edfd514bf66d0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223796"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (spécificateurs d'exceptions implicites)

Lorsque l’option **/Zc : implicitNoexcept** est spécifiée, le compilateur ajoute un spécificateur d’exception implicite [noexcept](../../cpp/noexcept-cpp.md) aux fonctions membres spéciales définies par le compilateur et aux destructeurs définis par l’utilisateur et à annulateurs. Par défaut, **/Zc : implicitNoexcept** est activé pour se conformer à la norme ISO c++ 11. La désactivation de cette option désactive implicitement **`noexcept`** sur les destructeurs définis par l’utilisateur et les dealloacators et les fonctions membres spéciales définies par le compilateur.

## <a name="syntax"></a>Syntaxe

> **/Zc : implicitNoexcept**[ **-** ]

## <a name="remarks"></a>Notes

**/Zc : implicitNoexcept** indique au compilateur de suivre la section 15,4 de la norme ISO c++ 11. Il ajoute implicitement un **`noexcept`** spécificateur d’exception à chaque fonction membre spéciale déclarée implicitement ou explicitement par défaut (le constructeur par défaut, le constructeur de copie, le constructeur de déplacement, le destructeur, l’opérateur d’assignation de copie ou l’opérateur d’assignation de déplacement) et chaque destructeur défini par l’utilisateur ou fonction annulateur. Un annulateur d'allocation défini par l'utilisateur possède un spécificateur d'exception `noexcept(true)` implicite. Pour les destructeurs définis par l'utilisateur, le spécificateur d'exception implicite est `noexcept(true)` à moins qu'une classe de base ou une classe membre contenue possède un destructeur qui n'est pas `noexcept(true)`. Pour les fonctions membres spéciales générées par le compilateur, si une fonction quelconque directement appelée par cette fonction est effectivement `noexcept(false)`, le spécificateur d'exception implicite est `noexcept(false)`. Sinon, le spécificateur d'exception implicite est `noexcept(true)`.

Le compilateur ne génère pas de spécificateur d’exception implicite pour les fonctions déclarées à l’aide de **`noexcept`** spécificateurs explicites ou d' **`throw`** un `__declspec(nothrow)` attribut.

Par défaut, **/Zc : implicitNoexcept** est activé. L’option [/permissive-](permissive-standards-conformance.md) n’a pas d’incidence sur **/Zc : implicitNoexcept**.

Si l’option est désactivée en spécifiant **/Zc : implicitNoexcept-**, aucun spécificateur d’exception implicite n’est généré par le compilateur. Ce comportement est le même que Visual Studio 2013, où les destructeurs et les annulateurs qui n’ont pas de spécificateurs d’exception pouvaient avoir des **`throw`** instructions. Par défaut, et quand **/Zc : implicitNoexcept** est spécifié, si une **`throw`** instruction est rencontrée au moment de l’exécution dans une fonction avec un spécificateur implicite `noexcept(true)` , elle provoque un appel immédiat de `std::terminate` et le comportement de déroulement normal pour les gestionnaires d’exceptions n’est pas garanti. Pour faciliter l’identification de cette situation, le compilateur génère un [Avertissement du compilateur (niveau 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Si le **`throw`** est intentionnel, nous vous recommandons de modifier votre déclaration de fonction pour qu’elle ait un `noexcept(false)` spécificateur explicite au lieu d’utiliser **/Zc : implicitNoexcept-**.

Cet exemple montre comment un destructeur défini par l’utilisateur qui n’a pas de spécificateur d’exception explicite se comporte lorsque l’option **/Zc : implicitNoexcept** est définie ou désactivée. Pour afficher le comportement lorsqu’il est défini, compilez à l’aide de `cl /EHsc /W4 implicitNoexcept.cpp` . Pour afficher le comportement quand il est désactivé, compilez à l’aide de `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` .

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

En cas de compilation à l’aide du paramètre par défaut **/Zc : implicitNoexcept**, l’exemple génère la sortie suivante :

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

En cas de compilation à l’aide du paramètre **/Zc : implicitNoexcept-**, l’exemple génère la sortie suivante :

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : implicitNoexcept** ou **/Zc : ImplicitNoexcept-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[pire](../../standard-library/exception-functions.md#terminate)<br/>
