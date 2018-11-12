---
title: _locking, constantes
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: 721e2433a6d7a76ad73b0f52f033c3e04cab8f6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526319"
---
# <a name="locking-constants"></a>_locking, constantes

## <a name="syntax"></a>Syntaxe

```
#include <sys/locking.h>
```

## <a name="remarks"></a>Notes

L’argument *mode* dans l’appel à la fonction `_locking` spécifie l’action de verrouillage à effectuer.

L’argument *mode* doit être une des constantes manifestes suivantes.

|||
|-|-|
| `_LK_LOCK`  | Verrouille les octets spécifiés. Si les octets ne peuvent pas être verrouillés, le la fonction réessaye après 1 seconde. Si, après 10 tentatives, les octets ne peuvent pas être verrouillés, la fonction retourne une erreur.  |
| `_LK_RLCK`  | Comme pour `_LK_LOCK`.  |
|`_LK_NBLCK`  | Verrouille les octets spécifiés. Si les octets ne peuvent pas être verrouillés, la fonction retourne une erreur.  |
| `_LK_NBRLCK`  | Comme pour `_LK_NBLCK`.  |
| `_LK_UNLCK`  | Déverrouille les octets spécifiés. (Les octets doivent avoir été préalablement verrouillés.)  |

## <a name="see-also"></a>Voir aussi

[_locking](../c-runtime-library/reference/locking.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)