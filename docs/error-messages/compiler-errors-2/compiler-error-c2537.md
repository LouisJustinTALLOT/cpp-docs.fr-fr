---
description: 'En savoir plus sur : erreur du compilateur C2537'
title: Erreur du compilateur C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 46603ded270b4702d4b7d4de97352547c5f503f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302034"
---
# <a name="compiler-error-c2537"></a>Erreur du compilateur C2537

'specifier' : spécification de liaison non conforme

Causes possibles :

1. Le spécificateur de liaison n’est pas pris en charge. Seul le spécificateur de liaison « C » est pris en charge.

1. La liaison « C » est spécifiée pour plusieurs fonctions dans un ensemble de fonctions surchargées. Cette opération n’est pas autorisée.

L’exemple suivant génère l’C2537 :

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
