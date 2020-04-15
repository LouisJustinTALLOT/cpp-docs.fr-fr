---
title: Manipulation d’exception dans MSVC
description: Aperçu de la gestion de l’exception de référence linguistique CMD.
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396275"
---
# <a name="exception-handling-in-msvc"></a>Manipulation d’exception dans MSVC

Une exception est une condition d’erreur, éventuellement en dehors du contrôle du programme, qui empêche le programme de se poursuivre selon son chemin d’exécution normal. Certaines opérations, y compris la création d’objets, l’entrée/sortie de fichiers et les appels de fonction effectués à partir d’autres modules, sont toutes des sources potentielles d’exceptions, même lorsque votre programme fonctionne correctement. Un code robuste vous permet d‘anticiper les exceptions et de les gérer. Pour détecter les erreurs logiques, utilisez des affirmations plutôt que des exceptions (voir [à l’aide d’affirmations).](/visualstudio/debugger/c-cpp-assertions)

## <a name="kinds-of-exceptions"></a>Types d’exceptions

Le compilateur Microsoft CMD (MSVC) prend en charge trois types de traitement des exceptions :

- [Manipulation d’exception de CMD](errors-and-exception-handling-modern-cpp.md)

   Pour la plupart des programmes de C, vous devez utiliser la manipulation des exceptions CMD. Il est sans danger de type, et s’assure que les destructeurs d’objets sont invoqués pendant le dénouement de la pile.

- [Gestion structurée des exceptions](structured-exception-handling-c-cpp.md)

   Windows fournit son propre mécanisme d’exception, appelé manipulation d’exception structurée (SEH). Il n’est pas recommandé pour la programmation de C ou MFC. Utilisez SEH uniquement dans les programmes C non MFC.

- [Exceptions MFC](../mfc/exception-handling-in-mfc.md)

   Depuis la version 3.0, MFC a utilisé des exceptions C. Il soutient toujours ses anciennes macros de manutention d’exception, qui sont similaires aux exceptions de Cmd dans la forme. Pour obtenir des conseils sur le mélange des macros MFC et des exceptions C, voir [Exceptions: Utilisation de macros MFC et exceptions C .](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

Utilisez une option de compilateur [/EH](../build/reference/eh-exception-handling-model.md) pour spécifier le modèle de manutention d’exception à utiliser dans un projet C. La gestion standard des exceptions de CMD **(/EHsc**) est la valeur par défaut dans les nouveaux projets de CMD dans Visual Studio.

Nous ne vous recommandons pas de mélanger les mécanismes de manutention des exceptions. Par exemple, n’utilisez pas d’exceptions CMD avec une manipulation d’exception structurée. L’utilisation d’une manipulation d’exception CMD rend votre code plus portable, et vous permet de gérer des exceptions de tout type. Pour plus d’informations sur les inconvénients du traitement structuré des exceptions, voir [Gestion d’exception structurée](structured-exception-handling-c-cpp.md).

## <a name="in-this-section"></a>Contenu de cette section

- [Pratiques exemplaires modernes de CMD pour les exceptions et le traitement des erreurs](errors-and-exception-handling-modern-cpp.md)

- [Comment concevoir pour la sécurité d’exception](how-to-design-for-exception-safety.md)

- [Comment établir une interface entre le code exceptionnel et le code non exceptionnel](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Instructions try, catch et throw](try-throw-and-catch-statements-cpp.md)

- [Évaluation des blocs catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions et dénouement de la pile](exceptions-and-stack-unwinding-in-cpp.md)

- [Spécifications des exceptions](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Exceptions C++ non gérées](unhandled-cpp-exceptions.md)

- [Mélange d’exceptions C (structurées) et d’exceptions C++](mixing-c-structured-and-cpp-exceptions.md)

- [Gestion structurée des exceptions (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](cpp-language-reference.md)</br>
[Gestion d'exceptions x64](../build/exception-handling-x64.md)</br>
[Manipulation d’exception (C/CLI et C/CX)](../extensions/exception-handling-cpp-component-extensions.md)
