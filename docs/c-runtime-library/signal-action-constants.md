---
title: Constantes d’action signal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs:
- C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2cb8e8ca907081e85be03d7576d0252cdf20ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081312"
---
# <a name="signal-action-constants"></a>signal, constantes action

L’action effectuée lors de la réception du signal d’interruption varie selon la valeur de `func`.

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Notes

L’argument `func` doit être une adresse de fonction ou une des constantes manifestes répertoriées ci-dessous et définies dans SIGNAL.H.

|||
|-|-|
| `SIG_DFL`  | Utilise la réponse par défaut du système. Si le programme appelant utilise des E/S de flux, les mémoires tampon créées par la bibliothèque Runtime ne sont pas vidées.  |
| `SIG_IGN`  | Ignore le signal d’interruption. Cette valeur ne doit jamais être donnée pour `SIGFPE`, car l’état à virgule flottante du processus reste non défini.  |
| `SIG_SGE`  | Indique qu’une erreur s’est produite dans le signal.  |
| `SIG_ACK`  | Indique qu’un accusé de réception a été reçu.  |
| `SIG_ERR`  | Un type de retour d’un signal indiquant une erreur s’est produite.  |

## <a name="see-also"></a>Voir aussi

[signal](../c-runtime-library/reference/signal.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)