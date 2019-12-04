---
title: Erreur du compilateur C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: 630e5b1cc6e99ffda28f50c09bccbbc2fea07172
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737697"
---
# <a name="compiler-error-c2612"></a>Erreur du compilateur C2612

« char » de fin non conforme dans la liste d’initialiseurs de base/membre

Un caractère apparaît après la dernière base ou membre d’une liste d’initialiseurs.

L’exemple suivant génère l’C2612 :

```cpp
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```
