---
description: 'En savoir plus sur : erreur irrécupérable C1016'
title: Erreur irrécupérable C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: e0f9a887c42c7006a31124446021ebee54225984
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262410"
---
# <a name="fatal-error-c1016"></a>Erreur irrécupérable C1016

\#ifdef identificateur attendu # ifndef identificateur attendu

La directive de compilation conditionnelle ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) ou `#ifndef`) n’a aucun identificateur à évaluer. Pour résoudre l’erreur, spécifiez un identificateur.

L’exemple suivant génère l’erreur C1016 :

```cpp
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

Solution possible :

```cpp
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```
