---
title: Erreur du compilateur C2760
ms.date: 11/04/2016
f1_keywords:
- C2760
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
ms.openlocfilehash: 5680de2fe0364d7cdc5e7ef017bd298423ea4c21
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273669"
---
# <a name="compiler-error-c2760"></a>Erreur du compilateur C2760

> erreur de syntaxe : '*nom1*'non'*nom2*'attendu

## <a name="remarks"></a>Notes

Il existe plusieurs façons de provoquer cette erreur. En règle générale, elle est provoquée par une séquence de jeton que le compilateur ne peut pas avoir de sens.

## <a name="example"></a>Exemples

Dans cet exemple, un opérateur de cast est utilisé avec un opérateur non valide.

```cpp
// C2760.cpp
class B {};
class D : public B {};

void f(B* pb) {
    D* pd1 = static_cast<D*>(pb);
    D* pd2 = static_cast<D*>=(pb);  // C2760
    D* pd3 = static_cast<D*=(pb);   // C2760
}
```
