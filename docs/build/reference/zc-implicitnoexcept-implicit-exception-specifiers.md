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
ms.openlocfilehash: 0ca03cc2a3afa0d5665f217ccb0d41eb1e41d3be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480927"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (spécificateurs d'exceptions implicites)

Lorsque le **/Zc : implicitnoexcept** est spécifiée, le compilateur ajoute implicite [noexcept](../../cpp/noexcept-cpp.md) spécificateur d’exception pour les fonctions membres spéciales définies par le compilateur et aux destructeurs définis par l’utilisateur et annulateurs d’allocation. Par défaut, **/Zc : implicitnoexcept** est activé pour être conforme à la norme C ++ 11 ISO. La désactivation de cette option désactive `noexcept` implicite sur les annulateurs d'allocation et les destructeurs définis par l'utilisateur et sur les fonctions membres spéciales définies par le compilateur.

## <a name="syntax"></a>Syntaxe

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>Notes

**/ Zc : implicitnoexcept** indique au compilateur de suivre la section 15.4 de la norme C ++ 11 ISO. Elle ajoute implicitement une `noexcept` spécificateur d’exception à chaque fonction membre spéciale déclarée implicitement ou explicitement par défaut, le constructeur par défaut, de copier le constructeur, constructeur de déplacement, destructeur, opérateur d’assignation de copie ou d’assignation de déplacement opérateur — et chaque fonction destructeur ou annulateur d’allocation définie par l’utilisateur. Un annulateur d'allocation défini par l'utilisateur possède un spécificateur d'exception `noexcept(true)` implicite. Pour les destructeurs définis par l'utilisateur, le spécificateur d'exception implicite est `noexcept(true)` à moins qu'une classe de base ou une classe membre contenue possède un destructeur qui n'est pas `noexcept(true)`. Pour les fonctions membres spéciales générées par le compilateur, si une fonction quelconque directement appelée par cette fonction est effectivement `noexcept(false)`, le spécificateur d'exception implicite est `noexcept(false)`. Sinon, le spécificateur d'exception implicite est `noexcept(true)`.

Le compilateur ne génère pas un spécificateur d'exception implicite pour les fonctions déclarées à l'aide de spécificateurs `noexcept` ou `throw` explicites ou d'un attribut `__declspec(nothrow)`.

Par défaut, **/Zc : implicitnoexcept** est activé. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc : implicitnoexcept**.

Si l’option est désactivée en spécifiant **/Zc:implicitNoexcept-**, aucun spécificateur d’exception implicite n’est générés par le compilateur. Ce comportement est identique à celui de Visual Studio 2013, où les destructeurs et les annulateurs d'allocation qui n'avaient pas de spécificateur d'exception pouvaient avoir des instructions `throw`. Par défaut et à quel moment **/Zc : implicitnoexcept** est spécifié, si un `throw` est rencontrée au moment de l’exécution dans une fonction avec implicite `noexcept(true)` spécificateur, elle provoque un appel immédiat de `std::terminate`, et le comportement de déroulement normal pour les gestionnaires d’exceptions n’est pas garanti. Pour aider à identifier cette situation, le compilateur génère [Avertissement du compilateur (niveau 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Si le `throw` est intentionnelle, nous vous recommandons de modifier votre déclaration de fonction pour avoir explicite `noexcept(false)` spécificateur au lieu d’utiliser **/Zc:implicitNoexcept-**.

Cet exemple montre comment un destructeur défini par l’utilisateur qui ne dispose d’aucun spécificateur d’exception explicite comporte lorsque le **/Zc : implicitnoexcept** option est définie ou désactivée. Pour afficher le comportement lorsque la valeur, compilez en utilisant `cl /EHsc /W4 implicitNoexcept.cpp`. Pour afficher le comportement lorsque désactivée, compilez en utilisant `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.

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

Lors de la compilation en utilisant le paramètre par défaut **/Zc : implicitnoexcept**, l’exemple génère la sortie :

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Lors de la compilation en utilisant le paramètre **/Zc:implicitNoexcept-**, l’exemple génère la sortie :

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : implicitnoexcept** ou **/Zc:implicitNoexcept-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate](../../standard-library/exception-functions.md#terminate)<br/>
