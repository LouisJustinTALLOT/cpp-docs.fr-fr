---
title: Constantes _locking | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abf776ab72d692be6d573803353f35946df145ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031928"
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