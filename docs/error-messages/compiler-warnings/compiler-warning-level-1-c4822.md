---
title: Avertissement du compilateur (niveau 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 02e7ba11f7bda134bcc98ce2c494a3ef367c0d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378503"
---
# <a name="compiler-warning-level-1-c4822"></a>Avertissement du compilateur (niveau 1) C4822

’membre’ : la fonction membre de classe locale n’a pas de corps

Une fonction membre de classe locale a été déclarée mais n’a pas été définie dans la classe. Pour utiliser une fonction membre de classe locale, vous devez la définir dans la classe. Vous ne pouvez pas la déclarer dans la classe et la définir hors classe.

Toute définition hors classe pour une fonction membre de classe locale constitue une erreur.

L’exemple suivant génère l’erreur C4822 :

```
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```