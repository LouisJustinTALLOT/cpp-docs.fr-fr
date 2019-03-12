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
ms.openlocfilehash: e9953e967d1c94ae56dfc1063fb0deafa342631c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738730"
---
# <a name="signal-constants"></a>signal, constantes

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Remarques

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
