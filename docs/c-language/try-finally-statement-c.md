---
title: try-finally, instruction (C)
description: Microsoft C/C++ implémente la gestion structurée des exceptions (SEH) à l’aide d’une extension de langage d’instruction try-finally.
ms.date: 08/24/2020
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 6f9cf901ed0a82b355880225c902ec4fc3e1082b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898714"
---
# <a name="try-finally-statement-c"></a>try-finally, instruction (C)

**Spécifique à Microsoft**

L'instruction `try-finally` est une extension Microsoft du langage C qui permet aux applications de garantir l'exécution du code de nettoyage lorsque l'exécution d'un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. L'instruction `try-finally` est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur qui peut provoquer un retour prématuré de la routine.

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

L’instruction composée après la **`__try`** clause est la section protégée. L’instruction composée après la **`__finally`** clause est le gestionnaire de terminaisons. Le gestionnaire spécifie un ensemble d’actions qui s’exécutent lorsque la section protégée est fermée. Peu importe si la section protégée est fermée par une exception (fin anormale) ou par un passage standard (fin normale).

Le contrôle atteint une **`__try`** instruction par exécution séquentielle simple (passage). Lorsque le contrôle entre dans l' **`__try`** instruction, son gestionnaire associé devient actif. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Le gestionnaire de terminaisons est appelé.

1. Une fois le gestionnaire de terminaisons terminé, l’exécution se poursuit après l' **`__finally`** instruction. Quelle que soit la façon dont la section protégée se termine (par exemple, via une **`goto`** instruction hors du corps protégé ou via une **`return`** instruction), le gestionnaire de terminaisons est exécuté avant que le déroulement du contrôle ne quitte la section protégée.

Le **`__leave`** mot clé est valide dans un `try-finally` bloc d’instructions. L’effet de **`__leave`** est d’accéder à la fin du `try-finally` bloc. Le gestionnaire de terminaisons est immédiatement exécuté. Bien qu’une **`goto`** instruction puisse être utilisée pour obtenir le même résultat, une **`goto`** instruction provoque le déroulement de la pile. L' **`__leave`** instruction est plus efficace car elle n’implique pas le déroulement de la pile.

Le fait de quitter une `try-finally` instruction à l’aide d’une **`return`** instruction ou de la `longjmp` fonction runtime est considéré comme un arrêt anormal. Il n’est pas légal de rentrer dans une **`__try`** instruction, mais d’en sortir. Toutes les **`__finally`** instructions qui sont actives entre le point de départ et la destination doivent être exécutées. Il s’agit d’un *déroulement local*.

Le gestionnaire de terminaisons n’est pas appelé si un processus est supprimé lors de l’exécution d’une `try-finally` instruction.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec les fichiers sources C et C++. Toutefois, elle n’est pas conçue spécifiquement pour C++. Pour les programmes C++ portables, la gestion des exceptions C++ doit être utilisée à la place de la gestion structurée des exceptions. En outre, le mécanisme de gestion des exceptions C++ est beaucoup plus souple, car il peut gérer les exceptions de tout type. Pour plus d’informations, consultez [gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md) dans la référence du *langage C++*.

Consultez l’exemple de l' [ `try-except` instruction](../c-language/try-except-statement-c.md) pour voir comment l' `try-finally` instruction fonctionne.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`try-finally` instruction (C++)](../cpp/try-finally-statement.md)
