---
description: 'En savoir plus sur : erreur du compilateur C2780'
title: Erreur du compilateur C2780
ms.date: 11/04/2016
f1_keywords:
- C2780
helpviewer_keywords:
- C2780
ms.assetid: 423793d8-a3b2-4f35-85f8-ae1d043e2b69
ms.openlocfilehash: 00b1117bdcae2559b7ec7c374f7b5ca403aa783c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298030"
---
# <a name="compiler-error-c2780"></a>Erreur du compilateur C2780

'déclaration' : N arguments attendus - M fournis

Un modèle de fonction a trop peu d’arguments ou trop d’arguments.

L'exemple suivant génère l'erreur C2780 et montre comment la corriger :

```cpp
// C2780.cpp
template<typename T>
void f(T, T){}

int main() {
   f(1);  // C2780
   // try the following line instead
   // f(1,2);
}
```
