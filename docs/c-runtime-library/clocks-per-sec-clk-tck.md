---
description: 'En savoir plus sur : CLOCKS_PER_SEC, CLK_TCK'
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: 43c59932a3026919435516fc0bfe88ef1e1e45ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322670"
---
# <a name="clocks_per_sec-clk_tck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Syntaxe

```
#include <time.h>
```

## <a name="remarks"></a>Notes

La durée en secondes est la valeur retournée par la fonction `clock`, divisée par `CLOCKS_PER_SEC`. `CLK_TCK` est équivalent, mais considéré comme obsolète.

## <a name="see-also"></a>Voir aussi

[24x7](../c-runtime-library/reference/clock.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
