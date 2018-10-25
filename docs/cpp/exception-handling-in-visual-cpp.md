---
title: Gestion des exceptions dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b168bf95e44a41973d92230f559246b03f275601
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073082"
---
# <a name="exception-handling-in-visual-c"></a>Gestion des exceptions en Visual C++

Une exception est une condition d’erreur, éventuellement en dehors du contrôle du programme, qui empêche le programme de se poursuivre selon son chemin d’exécution normal. Certaines opérations, notamment la création d'objet, l'entrée/la sortie de fichier et les appels de fonction créés à partir d'autres modules, sont toutes des sources potentielles d'exceptions même lorsque votre programme s'exécute correctement. Un code robuste vous permet d‘anticiper les exceptions et de les gérer.

Pour détecter les erreurs de logique dans un seul programme ou un module, utilisez les assertions plutôt que des exceptions (consultez [à l’aide des Assertions](/visualstudio/debugger/c-cpp-assertions)).

Visual C++ prend en charge trois types de gestion des exceptions :

- [Gestion des exceptions C++](../cpp/cpp-exception-handling.md)

   Pour la plupart des programmes C++, vous devez utiliser la gestion des exceptions C++, qui est de type sécurisé et garantit que les destructeurs d'objet sont appelés durant le déroulement de pile.

- [Gestion structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md)

   Windows fournit son propre mécanisme d'exception, appelé SEH. Il n'est pas recommandé pour la programmation C++ ou MFC. Utilisez SEH uniquement dans les programmes C non MFC.

- [Exceptions MFC](../mfc/exception-handling-in-mfc.md)

   Depuis la version 3.0, MFC utilise des exceptions C++ mais prend toujours en charge les macros plus anciennes de gestion des exceptions, qui sont similaires aux exceptions C++ en termes de format. Bien que ces macros ne soient pas recommandées pour une nouvelle programmation, elles sont toujours prises en charge pour la compatibilité descendante. Dans les programmes qui utilisent déjà les macros, vous pouvez également utiliser des exceptions C++. Pendant le prétraitement, les macros ont la valeur des mots clés de gestion des exceptions définis dans le cadre de l'implémentation Visual C++ du langage C++ à compter de Visual C++ version 2.0. Vous pouvez laisser les macros des exceptions existantes telles qu'elles sont lorsque vous commencez à utiliser des exceptions C++.

Utiliser le [/EH](../build/reference/eh-exception-handling-model.md) option du compilateur pour spécifier le type de gestion des exceptions pour l’utiliser dans un projet ; Gestion des exceptions C++ sont la valeur par défaut. Ne mélangez pas les mécanismes de gestion des erreurs. Par exemple, n'utilisez pas d'exceptions C++ avec la gestion structurée des exceptions. L'utilisation de la gestion des exceptions C++ rend votre code plus portable et vous permet de gérer des exceptions de tout type. Pour plus d’informations sur les inconvénients de la gestion structurée des exceptions, consultez [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Pour des conseils sur la combinaison des macros MFC et des exceptions C++, consultez [Exceptions : utilisation des Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Pour plus d’informations sur la gestion des exceptions dans les applications CLR, consultez [gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md).

Pour plus d’informations sur les exceptions sur x64 processeurs, consultez [(x64) gestion des exceptions](../build/exception-handling-x64.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)