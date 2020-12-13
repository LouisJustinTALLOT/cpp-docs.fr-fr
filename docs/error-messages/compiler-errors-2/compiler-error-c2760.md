---
description: 'En savoir plus sur : erreur du compilateur C2760'
title: Erreur du compilateur C2760
ms.date: 11/04/2016
f1_keywords:
- C2760
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
ms.openlocfilehash: bba26b68a2e4c98cf478098b2e44e82962afd9f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336160"
---
# <a name="compiler-error-c2760"></a>Erreur du compilateur C2760

> erreur de syntaxe : '*nom1*'non'*nom2*'attendu

## <a name="remarks"></a>Notes

Il existe plusieurs façons de provoquer cette erreur. En règle générale, elle est provoquée par une séquence de jeton que le compilateur ne peut pas avoir de sens.

## <a name="example"></a>Exemple

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
