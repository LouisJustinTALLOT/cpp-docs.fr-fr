---
title: Erreur du compilateur C2883 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2883
dev_langs:
- C++
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50cc5b2abb34fae21bea78aa146e74b9aa9491c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019261"
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