---
title: Avertissement du compilateur (niveau 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: 4da60194deaeac3c79f8c3e9be3bd87d91bc7ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487033"
---
# <a name="compiler-warning-level-1-c4730"></a>Avertissement du compilateur (niveau 1) C4730

« principal » : combinaison de _m64 et expressions peuvent entraîner un code erroné de virgule flottante

Utilise une fonction [__m64](../../cpp/m64.md) et **float**/**double** types. Espace du Registre, car les intrinsèques MMX et registres en virgule flottante partagent le même physique (ne peut pas être utilisés simultanément), à l’aide de `__m64` et **float**/**double** types dans le même fonction peut entraîner une altération des données, ce qui provoque peut-être une exception.

À utiliser en toute sécurité `__m64` types et les types à virgule flottante dans la même fonction, chaque instruction qui utilise un des types doit être séparée par le **_m_empty()** (pour MMX) ou **_m_femms()** (pour 3DNow !) intrinsèque.

L’exemple suivant génère l’erreur C4730 :

```
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