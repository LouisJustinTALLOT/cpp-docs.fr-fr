---
title: Erreur du compilateur C2847
ms.date: 11/04/2016
f1_keywords:
- C2847
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
ms.openlocfilehash: 99c49be746cea6fb80c5e24667bcd97556a0ad04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161041"
---
# <a name="compiler-error-c2847"></a>Erreur du compilateur C2847

impossible d'appliquer sizeof à un type managé ou WinRT 'classe'

Le [sizeof](../../cpp/sizeof-operator.md) opérateur Obtient la valeur d’un objet au moment de la compilation. La taille d'un type valeur, d'une interface ou d'une classe managée ou WinRT est dynamique et ne peut pas, par conséquent, être connue au moment de la compilation.

Par exemple, l'exemple suivant génère l'erreur C2847 :

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
