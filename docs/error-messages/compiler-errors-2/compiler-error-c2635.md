---
description: 'En savoir plus sur : erreur du compilateur C2635'
title: Erreur du compilateur C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 8ecc6faaefb3dea5f0cfcded4d6817a807580254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123381"
---
# <a name="compiler-error-c2635"></a>Erreur du compilateur C2635

Impossible de convertir’identificateur1 * 'en’identificateur2 \* '; la conversion à partir d’une classe de base virtuelle est implicite

La conversion nécessite un cast d’une **`virtual`** classe de base vers une classe dérivée, ce qui n’est pas autorisé.

L’exemple suivant génère l’C2635 :

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
