---
title: 'Timing of exception handling: A summary'
ms.date: 05/07/2019
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
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246336"
---
# <a name="timing-of-exception-handling-a-summary"></a>Timing of exception handling: A summary

A termination handler is executed no matter how the **__try** statement block is terminated. Causes include jumping out of the **__try** block, a `longjmp` statement that transfers control out of the block, and unwinding the stack due to exception handling.

> [!NOTE]
>  The Microsoft C++ compiler supports two forms of the `setjmp` and `longjmp` statements. La version rapide ignore la gestion du bloc de fin mais est plus efficace. To use this version, include the file \<setjmp.h>. L'autre version prend en charge la gestion du bloc de fin, comme il est décrit dans le paragraphe précédent. To use this version, include the file \<setjmpex.h>. L'augmentation des performances de la version rapide dépend de la configuration matérielle.

Le système d'exploitation exécute tous les gestionnaires de terminaisons dans l'ordre approprié avant que tout autre code soit exécuté, notamment le corps d'un gestionnaire d'exceptions.

Lorsque la cause de l'interruption est une exception, le système doit d'abord exécuter la partie de filtre d'un ou plusieurs gestionnaires d'exceptions avant de décider ce qui doit être terminé. L'ordre des événements est le suivant :

1. une exception est levée.

1. Le système examine la hiérarchie des gestionnaires d'exceptions actifs et applique le filtre du gestionnaire avec la priorité la plus élevée. C'est le gestionnaire d'exceptions dernièrement installé et le plus profondément imbriqué en termes de blocs et d'appels de fonction.

1. Si ce filtre passe la main (retourne 0), le processus se poursuit jusqu'à ce qu'il trouve un filtre qui ne passe pas la main.

1. If this filter returns -1, execution continues where the exception was raised, and no termination takes place.

1. Si le filtre retourne 1, les événements suivants se produisent :

   - Le système déroule la pile, effaçant tous les frames de pile entre le code en cours d'exécution (où l'exception a été levée) et le frame de pile qui contient le gestionnaire d'exceptions qui prend la main.

   - Au fur et à mesure que la pile est déroulée, chaque gestionnaire de terminaisons figurant sur la pile est exécuté.

   - Le gestionnaire d'exceptions lui-même est exécuté.

   - La ligne de code prend la main après la fin de ce gestionnaire d'exceptions.

## <a name="see-also"></a>Voir aussi

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)