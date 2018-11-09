---
title: _FREEENTRY, _USEDENTRY
ms.date: 11/04/2016
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
ms.openlocfilehash: 3bf05807930373a905a5bf71cf4ebc1f119056a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513982"
---
# <a name="freeentry-usedentry"></a>_FREEENTRY, _USEDENTRY

## <a name="syntax"></a>Syntaxe

```
#include <malloc.h>
```

## <a name="remarks"></a>Notes

Ces constantes représentent les valeurs affectées par les routines `_heapwalk` à l’élément **_useflag** de la structure **_HEAPINFO**. Ils indiquent l’état de l’entrée de tas.

## <a name="see-also"></a>Voir aussi

[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)