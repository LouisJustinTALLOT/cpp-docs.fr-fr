---
description: 'En savoir plus sur : erreur du compilateur C2784'
title: Erreur du compilateur C2784
ms.date: 11/04/2016
f1_keywords:
- C2784
helpviewer_keywords:
- C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
ms.openlocfilehash: dcee0cc2c6c8154bafe4a37fe83c66b1c8d477d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297913"
---
# <a name="compiler-error-c2784"></a>Erreur du compilateur C2784

’déclaration’ : impossible de déduire l’argument template pour ’type’ à partir de ’type’

Le compilateur ne peut pas déterminer un argument template à partir des arguments de fonction fournis.

L'exemple suivant génère l'erreur C2784 et montre comment la corriger :

```cpp
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
