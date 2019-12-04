---
title: Erreur du compilateur C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: f3868a44cf04d6c87092759ea473aa78aa0ad4c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760887"
---
# <a name="compiler-error-c2892"></a>Erreur du compilateur C2892

la classe locale ne doit pas avoir de modèles membres

Les fonctions membres basées sur un modèle ne sont pas valides dans une classe définie dans une fonction.

L’exemple suivant génère l’C2892 :

```cpp
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```
