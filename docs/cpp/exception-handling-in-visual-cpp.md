---
title: Gestion des exceptions dans MSVC
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
# <a name="exception-handling-in-msvc"></a>Gestion des exceptions dans MSVC

Une exception est une condition d’erreur, éventuellement en dehors du contrôle du programme, qui empêche le programme de se poursuivre selon son chemin d’exécution normal. Certaines opérations, notamment la création d'objet, l'entrée/la sortie de fichier et les appels de fonction créés à partir d'autres modules, sont toutes des sources potentielles d'exceptions même lorsque votre programme s'exécute correctement. Un code robuste vous permet d‘anticiper les exceptions et de les gérer. Pour détecter les erreurs de logique, utilisez des assertions plutôt que des exceptions (consultez [utilisation d’assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Genres d’exceptions

Le compilateur C++ Microsoft (MSVC) prend en charge trois types de gestion des exceptions :

- [C++gestion des exceptions](errors-and-exception-handling-modern-cpp.md)

   Pour la plupart des programmes C++, vous devez utiliser la gestion des exceptions C++, qui est de type sécurisé et garantit que les destructeurs d'objet sont appelés durant le déroulement de pile.

- [Gestion structurée des exceptions](structured-exception-handling-c-cpp.md)

   Windows fournit son propre mécanisme d'exception, appelé SEH. Il n'est pas recommandé pour la programmation C++ ou MFC. Utilisez SEH uniquement dans les programmes C non-MFC.

- [Exceptions MFC](../mfc/exception-handling-in-mfc.md)

Utilisez l’option du compilateur [/Eh](../build/reference/eh-exception-handling-model.md) pour spécifier le type de gestion des exceptions à utiliser dans un projet. C++ la gestion des exceptions est la valeur par défaut. Ne mélangez pas les mécanismes de gestion des erreurs. Par exemple, n'utilisez pas d'exceptions C++ avec la gestion structurée des exceptions. L'utilisation de la gestion des exceptions C++ rend votre code plus portable et vous permet de gérer des exceptions de tout type. Pour plus d’informations sur les inconvénients de la gestion structurée des exceptions, consultez [gestion structurée des exceptions](structured-exception-handling-c-cpp.md). Pour obtenir des conseils sur la combinaison des C++ macros MFC et des exceptions, consultez [exceptions : C++ utilisation de macros MFC et d’exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>Dans cette section

- [Meilleures C++ pratiques modernes pour les exceptions et la gestion des erreurs](errors-and-exception-handling-modern-cpp.md)

- [Comment concevoir la sécurité des exceptions](how-to-design-for-exception-safety.md)

- [Comment établir une interface entre du code exceptionnel et non exceptionnel](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Instructions Try, catch et Throw](try-throw-and-catch-statements-cpp.md)

- [Évaluation des blocs catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions et déroulement de pile](exceptions-and-stack-unwinding-in-cpp.md)

- [Spécifications des exceptions](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Exceptions C++ non gérées](unhandled-cpp-exceptions.md)

- [Mélange d’exceptions C (structurées) et d’exceptions C++](mixing-c-structured-and-cpp-exceptions.md)

- [Gestion structurée des exceptions (SEH) (C++C/)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](cpp-language-reference.md)</br>
[Gestion d'exceptions x64](../build/exception-handling-x64.md)</br>
[Gestion des exceptionsC++(/CLI C++et/CX)](../extensions/exception-handling-cpp-component-extensions.md)
