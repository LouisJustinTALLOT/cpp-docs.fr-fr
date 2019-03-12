---
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750674"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Syntaxe

```
#include <time.h>
```

## <a name="remarks"></a>Remarques

La durée en secondes est la valeur retournée par la fonction `clock`, divisée par `CLOCKS_PER_SEC`. `CLK_TCK` est équivalent, mais considéré comme obsolète.

## <a name="see-also"></a>Voir aussi

[horloge](../c-runtime-library/reference/clock.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
