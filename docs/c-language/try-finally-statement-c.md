---
title: try-finally, instruction (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: b800daa7689cef769ce3a3b070c957f18e8794c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213708"
---
# <a name="try-finally-statement-c"></a>try-finally, instruction (C)

**Spécifique à Microsoft**

L'instruction `try-finally` est une extension Microsoft du langage C qui permet aux applications de garantir l'exécution du code de nettoyage lorsque l'exécution d'un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. L'instruction `try-finally` est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur qui peut provoquer un retour prématuré de la routine.

*try-finally-statement*: **__try**  *compound-statement*

**`__finally`**  *Compound-Statement*

L'instruction composée après la clause `__try` est la section protégée. L’instruction composée après la **`__finally`** clause est le gestionnaire de terminaisons. Le gestionnaire spécifie un jeu d'actions qui s'exécutent lorsque la section protégée est fermée, que la section protégée soit fermée par une exception (fin anormale) ou par un passage standard (fin normale).

Le contrôle atteint une instruction `__try` par exécution séquentielle simple (passage). Lorsque le contrôle pénètre dans l'instruction `__try`, son gestionnaire associé devient actif. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Le gestionnaire de terminaisons est appelé.

1. Une fois le gestionnaire de terminaisons terminé, l’exécution se poursuit après l' **`__finally`** instruction. Quelle que soit la façon dont la section protégée se termine (par exemple, via une **`goto`** instruction hors du corps protégé ou via une **`return`** instruction), le gestionnaire de terminaisons est exécuté avant que le workflow de contrôle ne quitte la section protégée.

Le ** `__leave** keyword is valid within a ` ` statement block. The effect of **` __leave try-finally** est d’accéder à la fin du `try-finally` bloc. Le gestionnaire de terminaisons est immédiatement exécuté. Bien qu’une **`goto`** instruction puisse être utilisée pour obtenir le même résultat, une **`goto`** instruction provoque le déroulement de la pile. L’instruction **' __leave** est plus efficace car elle n’implique pas le déroulement de la pile.

Le fait de quitter une `try-finally` instruction à l’aide d’une **`return`** instruction ou de la `longjmp` fonction runtime est considéré comme un arrêt anormal. Il est non conforme de sauter dans une instruction `__try`, mais conforme d'en sortir d'une. Toutes les **`__finally`** instructions qui sont actives entre le point de départ et la destination doivent être exécutées. Cela s'appelle un « déroulement local ».

Le gestionnaire de terminaisons n'est pas appelé si un processus est tué tout en exécutant une instruction `try-finally`.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, le mécanisme de gestion des exceptions C++ est beaucoup plus souple, car il peut gérer les exceptions de tout type.

> [!NOTE]
> Pour les programmes C++, la gestion des exceptions C++ doit être utilisée à la place de la gestion structurée des exceptions. Pour plus d’informations, consultez [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md) dans le *Guide de référence du langage C++*.

Consultez l'exemple pour [l'instruction try-except](../c-language/try-except-statement-c.md) pour voir comment l'instruction `try-finally` fonctionne.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[try-finally, instruction](../cpp/try-finally-statement.md)
