---
description: En savoir plus sur les constantes d’action de signal
title: signal, constantes action
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 380fed21b097b674958c6e2aae2f6b8c53845943
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276983"
---
# <a name="signal-action-constants"></a>signal, constantes action

L’action effectuée lors de la réception du signal d’interruption varie selon la valeur de `func`.

## <a name="syntax"></a>Syntaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Notes

L’argument `func` doit être une adresse de fonction ou une des constantes manifestes répertoriées ci-dessous et définies dans SIGNAL.H.

|Constante|Description|
|-|-|
| `SIG_DFL`  | Utilise la réponse par défaut du système. Si le programme appelant utilise des E/S de flux, les mémoires tampon créées par la bibliothèque Runtime ne sont pas vidées.  |
| `SIG_IGN`  | Ignore le signal d’interruption. Cette valeur ne doit jamais être donnée pour `SIGFPE`, car l’état à virgule flottante du processus reste non défini.  |
| `SIG_SGE`  | Indique qu’une erreur s’est produite dans le signal.  |
| `SIG_ACK`  | Indique qu’un accusé de réception a été reçu.  |
| `SIG_ERR`  | Un type de retour d’un signal indiquant une erreur s’est produite.  |

## <a name="see-also"></a>Voir aussi

[signal](../c-runtime-library/reference/signal.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
