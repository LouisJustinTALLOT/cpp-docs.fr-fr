---
title: 'Synchronisation de la gestion des exceptions : Un résumé'
description: Le minutage et l’ordre d’exécution de la gestion des exceptions dans Microsoft C++.
ms.date: 08/24/2020
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 2ce501d8d74b6f0f7ca92e193c39f8ce58a66053
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898356"
---
# <a name="timing-of-exception-handling-a-summary"></a>Synchronisation de la gestion des exceptions : Un résumé

Un gestionnaire de terminaisons est exécuté, quelle que soit la façon dont le **`__try`** bloc d’instructions est terminé. Les causes incluent le saut hors du **`__try`** bloc, une `longjmp` instruction qui transfère le contrôle hors du bloc et le déroulement de la pile en raison de la gestion des exceptions.

> [!NOTE]
> Le compilateur Microsoft C++ prend en charge deux formes `setjmp` d' `longjmp` instructions et. La version rapide ignore la gestion du bloc de fin mais est plus efficace. Pour utiliser cette version, incluez le fichier \<setjmp.h> . L'autre version prend en charge la gestion du bloc de fin, comme il est décrit dans le paragraphe précédent. Pour utiliser cette version, incluez le fichier \<setjmpex.h> . L'augmentation des performances de la version rapide dépend de la configuration matérielle.

Le système d'exploitation exécute tous les gestionnaires de terminaisons dans l'ordre approprié avant que tout autre code soit exécuté, notamment le corps d'un gestionnaire d'exceptions.

Lorsque la cause de l'interruption est une exception, le système doit d'abord exécuter la partie de filtre d'un ou plusieurs gestionnaires d'exceptions avant de décider ce qui doit être terminé. L'ordre des événements est le suivant :

1. une exception est levée.

1. Le système examine la hiérarchie des gestionnaires d’exceptions actifs et exécute le filtre du gestionnaire avec la priorité la plus élevée. C’est le gestionnaire d’exceptions le plus récemment installé et le plus profondément imbriqué, en passant par les blocs et les appels de fonction.

1. Si ce filtre passe le contrôle (retourne 0), le processus se poursuit jusqu’à ce qu’un filtre qui ne passe pas le contrôle soit trouvé.

1. Si ce filtre retourne-1, l’exécution continue là où l’exception a été levée et aucun arrêt n’a lieu.

1. Si le filtre retourne 1, les événements suivants se produisent :

   - Le système déroule la pile : il efface tous les frames de pile entre l’endroit où l’exception a été levée et le frame de pile qui contient le gestionnaire d’exceptions.

   - Au fur et à mesure que la pile est déroulée, chaque gestionnaire de terminaisons figurant sur la pile est exécuté.

   - Le gestionnaire d'exceptions lui-même est exécuté.

   - La ligne de code prend la main après la fin de ce gestionnaire d'exceptions.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire des arrêts](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
