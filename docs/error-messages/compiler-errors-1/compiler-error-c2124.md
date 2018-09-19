---
title: Erreur du compilateur C2124 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2124
dev_langs:
- C++
helpviewer_keywords:
- C2124
ms.assetid: 93392aaa-5582-4d68-8cc5-bd9c62a0ae7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7810565a8f7bfdac49f2c53815b9063e2e034df7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062318"
---
# <a name="compiler-error-c2124"></a>Erreur du compilateur C2124

division ou modulo par zéro

Une expression constante a un dénominateur égal à zéro. Pour résoudre l’erreur, ne divisez pas par zéro.

L’exemple suivant génère l’erreur C2124 :

```
// C2124.cpp
int main() {
  int i = 1 / 0;   // C2124  do not divide by zero
  int i2 = 12 / 2;   // OK
}
```