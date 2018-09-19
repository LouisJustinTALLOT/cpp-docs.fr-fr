---
title: Erreur du compilateur C2784 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2784
dev_langs:
- C++
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed0e5dd7628031a7ad5ac66d2b691ee52dda62f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091307"
---
# <a name="compiler-error-c2784"></a>Erreur du compilateur C2784

’déclaration’ : impossible de déduire l’argument template pour ’type’ à partir de ’type’

Le compilateur ne peut pas déterminer un argument template à partir des arguments de fonction fournis.

L'exemple suivant génère l'erreur C2784 et montre comment la corriger :

```
// C2784.cpp
template<class T> class X {};
template<class T> void f(X<T>) {}

int main() {
   X<int> x;
   f(1);   // C2784

   // To fix it, try the following line instead
   f(x);
}
```