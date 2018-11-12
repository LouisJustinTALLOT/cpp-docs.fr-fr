---
title: Erreur du compilateur C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: b61ad65555b5d5232468206f6170223c5f160a34
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556687"
---
# <a name="compiler-error-c2584"></a>Erreur du compilateur C2584

'Class' : diriger base 'Base2' n’est pas accessible ; déjà une base de 'Base1'

`Class` déjà dérive directement `Base1`. `Base2` dérive également de `Base1`. `Class` Impossible de dériver `Base2` car cela équivaudrait héritant (indirectement) `Base1` là encore, ce qui n’est pas légal, car `Base1` est déjà une classe de base directe.

## <a name="example"></a>Exemple

L’exemple suivant génère C2584.

```
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```