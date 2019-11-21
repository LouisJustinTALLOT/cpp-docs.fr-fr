---
title: Exception handling in MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246593"
---
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

Une exception est une condition d’erreur, éventuellement en dehors du contrôle du programme, qui empêche le programme de se poursuivre selon son chemin d’exécution normal. Certaines opérations, notamment la création d'objet, l'entrée/la sortie de fichier et les appels de fonction créés à partir d'autres modules, sont toutes des sources potentielles d'exceptions même lorsque votre programme s'exécute correctement. Un code robuste vous permet d‘anticiper les exceptions et de les gérer. To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   Pour la plupart des programmes C++, vous devez utiliser la gestion des exceptions C++, qui est de type sécurisé et garantit que les destructeurs d'objet sont appelés durant le déroulement de pile.

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   Windows fournit son propre mécanisme d'exception, appelé SEH. Il n'est pas recommandé pour la programmation C++ ou MFC. Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. Ne mélangez pas les mécanismes de gestion des erreurs. Par exemple, n'utilisez pas d'exceptions C++ avec la gestion structurée des exceptions. L'utilisation de la gestion des exceptions C++ rend votre code plus portable et vous permet de gérer des exceptions de tout type. For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>Dans cette section

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Évaluation des blocs catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Exceptions C++ non gérées](unhandled-cpp-exceptions.md)

- [Mélange d’exceptions C (structurées) et d’exceptions C++](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](cpp-language-reference.md)</br>
[Gestion d'exceptions x64](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
