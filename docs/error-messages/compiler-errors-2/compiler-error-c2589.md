---
title: Erreur du compilateur C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748500"
---
# <a name="compiler-error-c2589"></a>Erreur du compilateur C2589

'identificateur' : jeton non conforme à droite de' :: '

Si un nom de classe, de structure ou d’Union apparaît à gauche de l’opérateur de résolution de portée (deux-points), le jeton à droite doit être un membre de classe, de structure ou d’Union. Dans le cas contraire, tous les identificateurs globaux peuvent apparaître à droite.

L’opérateur de résolution de portée ne peut pas être surchargé.

L’exemple suivant génère l’C2589 :

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
