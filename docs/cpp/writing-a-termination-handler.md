---
title: Écriture d'un gestionnaire des terminaisons
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
ms.openlocfilehash: f0b994075a8d59ce5d0955f10bf8c61d357d2db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209466"
---
# <a name="writing-a-termination-handler"></a>Écriture d'un gestionnaire des terminaisons

Contrairement à un gestionnaire d'exceptions, un gestionnaire de terminaisons est toujours exécuté, que le bloc de code protégé soit terminé normalement ou non. L'objectif unique du gestionnaire de terminaisons doit être de garantir que les ressources, telles que la mémoire, les handles et les fichiers, sont fermées correctement indépendamment de la façon dont se termine l'exécution d'une section de code.

Les gestionnaires de terminaisons utilisent l'instruction try-finally.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [L’instruction try-finally](../cpp/try-finally-statement.md)

- [Nettoyage des ressources](../cpp/cleaning-up-resources.md)

- [Minutage des actions dans la gestion des exceptions](../cpp/timing-of-exception-handling-a-summary.md)

- [Restrictions sur les gestionnaires de terminaisons](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>Voir aussi

[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)