---
title: Erreur du compilateur C2158
ms.date: 11/04/2016
f1_keywords:
- C2158
helpviewer_keywords:
- C2158
ms.assetid: 39028899-e95c-4809-8e65-6111118641ee
ms.openlocfilehash: a84c803d45184c19bab0f855ae1eb33744c4e02d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597390"
---
# <a name="compiler-error-c2158"></a>Erreur du compilateur C2158

'type' : la directive #pragma make_public est actuellement prise en charge pour les types sans modèle natifs uniquement

Le pragma [make_public](../../preprocessor/make-public.md) est uniquement applicable à un type non-modèle natif.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2158.

```
// C2158.cpp
// compile with: /clr /c
ref class A {};
#pragma make_public(A)   // C2158

template< typename T >
class B {};
#pragma make_public(B)   // C2158
#pragma make_public(B<int>)   // C2158

void C () {}
#pragma make_public(C)   // C2158

class D {};
#pragma make_public(D)   // OK
```