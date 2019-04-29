---
title: Erreur du compilateur C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: 3f32307e519394433927d49aa92333fdff7b70f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378867"
---
# <a name="compiler-error-c2883"></a>Erreur du compilateur C2883

'name' : déclaration de fonction est en conflit avec 'identificateur' introduit par une déclaration using

Vous avez essayé de définir une fonction plusieurs fois. La première définition a été effectuée à partir d’un espace de noms avec un `using` déclaration. La deuxième était une définition locale.

L’exemple suivant génère l’erreur C2883 :

```
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```