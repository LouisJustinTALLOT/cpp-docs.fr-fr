---
description: 'En savoir plus sur : erreur du compilateur C2883'
title: Erreur du compilateur C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 2ff905f5f1ca8fea4f175799e576e4538bbab164
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332345"
---
# <a name="compiler-error-c2883"></a>Erreur du compilateur C2883

'name' : la déclaration de fonction est en conflit avec’identifier’introduit par une déclaration using

Vous avez essayé de définir une fonction plusieurs fois. La première définition a été effectuée à partir d’un espace de noms avec une **`using`** déclaration. La seconde était une définition locale.

L’exemple suivant génère l’C2883 :

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
