---
title: Gestion des exceptions dans MSVC
ms.date: 05/07/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 47443f1b7021aac7755d77f797a4f7b7410281f8
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222065"
---
# <a name="exception-handling-in-msvc"></a>Gestion des exceptions dans MSVC

Une exception est une condition d’erreur, éventuellement en dehors du contrôle du programme, qui empêche le programme de se poursuivre selon son chemin d’exécution normal. Certaines opérations, notamment la création d'objet, l'entrée/la sortie de fichier et les appels de fonction créés à partir d'autres modules, sont toutes des sources potentielles d'exceptions même lorsque votre programme s'exécute correctement. Un code robuste vous permet d‘anticiper les exceptions et de les gérer.

Pour détecter les erreurs de logique dans un seul programme ou un module, utilisez les assertions plutôt que des exceptions (consultez [à l’aide des Assertions](/visualstudio/debugger/c-cpp-assertions)).

Microsoft C++ compilateur (MSVC) prend en charge trois types de gestion des exceptions :

- [Gestion des exceptions C++](../cpp/cpp-exception-handling.md)

   Pour la plupart des programmes C++, vous devez utiliser la gestion des exceptions C++, qui est de type sécurisé et garantit que les destructeurs d'objet sont appelés durant le déroulement de pile.

- [Gestion structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md)

   Windows fournit son propre mécanisme d'exception, appelé SEH. Il n'est pas recommandé pour la programmation C++ ou MFC. Utilisez SEH uniquement dans les programmes C non MFC.

- [Exceptions MFC](../mfc/exception-handling-in-mfc.md)

   Depuis la version 3.0, MFC utilise des exceptions C++ mais prend toujours en charge les macros plus anciennes de gestion des exceptions, qui sont similaires aux exceptions C++ en termes de format. Bien que ces macros ne soient pas recommandées pour une nouvelle programmation, elles sont toujours prises en charge pour la compatibilité descendante. Dans les programmes qui utilisent déjà les macros, vous pouvez également utiliser des exceptions C++. Pendant le prétraitement, les macros ont la gestion des mots clés définis dans l’implémentation de MSVC d’exceptions le C++ langage depuis Visual C++ version 2.0. Vous pouvez laisser les macros des exceptions existantes telles qu'elles sont lorsque vous commencez à utiliser des exceptions C++.

Utiliser le [/EH](../build/reference/eh-exception-handling-model.md) option du compilateur pour spécifier le type de gestion des exceptions pour l’utiliser dans un projet ; Gestion des exceptions C++ sont la valeur par défaut. Ne mélangez pas les mécanismes de gestion des erreurs. Par exemple, n'utilisez pas d'exceptions C++ avec la gestion structurée des exceptions. L'utilisation de la gestion des exceptions C++ rend votre code plus portable et vous permet de gérer des exceptions de tout type. Pour plus d’informations sur les inconvénients de la gestion structurée des exceptions, consultez [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Pour des conseils sur la combinaison des macros MFC et des exceptions C++, consultez [Exceptions : À l’aide de Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Pour plus d’informations sur la gestion des exceptions dans les applications CLR, consultez [gestion des exceptions (C++ / c++ / CLI et c++ / CX)](../extensions/exception-handling-cpp-component-extensions.md).

Pour plus d’informations sur les exceptions sur x64 processeurs, consultez [x64 gestion des exceptions](../build/exception-handling-x64.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)