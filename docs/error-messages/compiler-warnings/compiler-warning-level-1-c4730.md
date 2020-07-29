---
title: Avertissement du compilateur (niveau 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: a132dcc795d6055c854a5ad147940868fe4e088b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228776"
---
# <a name="compiler-warning-level-1-c4730"></a>Avertissement du compilateur (niveau 1) C4730

'main' : le mélange d' _m64 et d’expressions à virgule flottante peut entraîner un code incorrect

Une fonction utilise [__m64](../../cpp/m64.md) et les **`float`** / **`double`** types. Étant donné que les registres MMX et à virgule flottante partagent le même espace de registre physique (ne peut pas être utilisé simultanément), l’utilisation des **`__m64`** **`float`** / **`double`** types et dans la même fonction peut entraîner une altération des données, provoquant éventuellement une exception.

Pour utiliser en toute sécurité des types **`__m64`** et des types à virgule flottante dans la même fonction, chaque instruction qui utilise l’un des types doit être séparée par le **_m_empty ()** (pour MMX) ou **_m_femms ()** (pour 3DNow !) intrinsèque.

L’exemple suivant génère l’C4730 :

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```
