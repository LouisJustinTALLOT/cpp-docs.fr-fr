---
title: Erreur du compilateur C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386939"
---
# <a name="compiler-error-c2589"></a>Erreur du compilateur C2589

'identificateur' : jeton non conforme à droite de ' ::'

Si un nom de classe, structure ou union apparaît à gauche de l’opérateur de résolution de portée (double deux-points), le jeton à droite doit être une classe, une structure ou un membre d’union. Sinon, n’importe quel identificateur global peut apparaître sur la droite.

L’opérateur de résolution de portée ne peut pas être surchargé.

L’exemple suivant génère l’erreur C2589 :

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```