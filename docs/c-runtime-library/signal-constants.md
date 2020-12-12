---
description: En savoir plus sur les constantes signal
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
ms.openlocfilehash: 57615e3a694ae24c0bfefe42b6a8ddd1de2a55ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276996"
---
# <a name="signal-constants"></a>signal, constantes

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Notes

L’argument `sig` doit être une des constantes manifestes répertoriées ci-dessous (définies dans SIGNAL.H).

|Constante|Description|
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
