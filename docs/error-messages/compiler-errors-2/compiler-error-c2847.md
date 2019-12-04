---
title: Erreur du compilateur C2847
ms.date: 11/04/2016
f1_keywords:
- C2847
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
ms.openlocfilehash: b8b31dc461c1d589151701c6946f6ac1a95c5517
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738984"
---
# <a name="compiler-error-c2847"></a>Erreur du compilateur C2847

impossible d'appliquer sizeof à un type managé ou WinRT 'classe'

L’opérateur [sizeof](../../cpp/sizeof-operator.md) obtient la valeur d’un objet au moment de la compilation. La taille d'un type valeur, d'une interface ou d'une classe managée ou WinRT est dynamique et ne peut pas, par conséquent, être connue au moment de la compilation.

Par exemple, l'exemple suivant génère l'erreur C2847 :

```cpp
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
