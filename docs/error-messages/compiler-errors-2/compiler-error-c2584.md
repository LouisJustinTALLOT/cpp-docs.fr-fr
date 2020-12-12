---
description: 'En savoir plus sur : erreur du compilateur C2584'
title: Erreur du compilateur C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: 7820019c3ec49928f59980adbd9ec814d67c3499
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177677"
---
# <a name="compiler-error-c2584"></a>Erreur du compilateur C2584

'Classe' : la base directe’base2 'est inaccessible ; une base de’Base1 'est déjà

`Class` dérive déjà directement de `Base1` . `Base2` dérive également de `Base1` . `Class` Impossible de dériver de `Base2` car cela signifierait hériter (indirectement) de `Base1` nouveau, ce qui n’est pas légal, car `Base1` est déjà une classe de base directe.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2584.

```cpp
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
