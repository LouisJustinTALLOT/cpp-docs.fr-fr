---
description: 'En savoir plus sur : erreur du compilateur C2691'
title: Erreur du compilateur C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 575651d1da871a0514585fea010ef3fe98e8a3cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344326"
---
# <a name="compiler-error-c2691"></a>Erreur du compilateur C2691

'Data type' : un managé ou un WinRTarray ne peut pas avoir ce type d’élément

Le type d'un élément de tableau managé ou WinRT peut être un type valeur ou un type référence.

L'exemple suivant génère l'erreur C2691 :

```cpp
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```
