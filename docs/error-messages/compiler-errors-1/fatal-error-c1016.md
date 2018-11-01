---
title: Erreur irrécupérable C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: 7463c6962817716611f3571e073712f374773fa7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566034"
---
# <a name="fatal-error-c1016"></a>Erreur irrécupérable C1016

\#ifdef identificateur attendu que #ifndef identificateur attendu

La directive de compilation conditionnelle ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) ou `#ifndef`) n’a aucun identificateur à évaluer. Pour résoudre l’erreur, spécifiez un identificateur.

L’exemple suivant génère l’erreur C1016 :

```
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

Solution possible :

```
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```