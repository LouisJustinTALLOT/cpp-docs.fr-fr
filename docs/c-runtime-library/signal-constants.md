---
title: signal, constantes
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: 1046a12fa0f250b348e6ff171c8865e3eb5ff4b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482659"
---
# <a name="signal-constants"></a>signal, constantes

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Notes

L’argument `sig` doit être une des constantes manifestes répertoriées ci-dessous (définies dans SIGNAL.H).

|||
|-|-|
|SIGABRT|Arrêt anormal. L’action par défaut termine le programme appelant avec le code de sortie 3.  |
|SIGABRT_COMPAT|Identique à SIGABRT. Pour la compatibilité avec les autres plateformes.  |
|SIGFPE|Erreur de virgule flottante, comme le dépassement de capacité, la division par zéro ou une opération non valide. L’action par défaut termine le programme appelant.  |
|SIGILL|Instruction non conforme. L’action par défaut termine le programme appelant.  |
|SIGINT|Interruption CTRL+C. L’action par défaut termine le programme appelant avec le code de sortie 3.  |
|SIGSEGV|Accès au stockage non conforme. L’action par défaut termine le programme appelant.  |
|SIGTERM|Demande d’arrêt envoyée au programme. L’action par défaut termine le programme appelant avec le code de sortie 3.  |
|SIG_ERR|Un type de retour d’un signal indiquant une erreur s’est produite.  |

## <a name="see-also"></a>Voir aussi

[signal](../c-runtime-library/reference/signal.md)<br/>
[raise](../c-runtime-library/reference/raise.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)