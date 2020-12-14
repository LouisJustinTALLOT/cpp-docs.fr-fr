---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4822'
title: Avertissement du compilateur (niveau 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 8e5fe62d70243da0121d58e553c500e5a079022a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198048"
---
# <a name="compiler-warning-level-1-c4822"></a>Avertissement du compilateur (niveau 1) C4822

’membre’ : la fonction membre de classe locale n’a pas de corps

Une fonction membre de classe locale a été déclarée mais n’a pas été définie dans la classe. Pour utiliser une fonction membre de classe locale, vous devez la définir dans la classe. Vous ne pouvez pas la déclarer dans la classe et la définir hors classe.

Toute définition hors classe pour une fonction membre de classe locale constitue une erreur.

L’exemple suivant génère l’erreur C4822 :

```cpp
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
