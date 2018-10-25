---
title: Constantes signal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs:
- C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: defd5f630f1d3832014e2cc7e9746c0e00e8d816
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070663"
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