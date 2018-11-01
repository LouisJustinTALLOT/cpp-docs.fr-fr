---
title: Avertissement du compilateur (niveau 1) C4556
ms.date: 08/27/2018
f1_keywords:
- xml
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 53261b97249340ce56ce6ae0f5cc0eab7e97a107
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538487"
---
# <a name="compiler-warning-level-1-c4556"></a>Avertissement du compilateur (niveau 1) C4556

> valeur d’argument immédiat intrinsèque '*valeur*'est hors limites'*limite_supérieure* - *LimiteSupérieure*'

## <a name="remarks"></a>Notes

Un intrinsèque correspond à une instruction de matériel. L’instruction matérielle a un nombre fixe de bits pour coder la constante. Si *valeur* est hors limites, elle ne sera pas codée correctement. Le compilateur tronque les bits supplémentaires.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4556 :

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```