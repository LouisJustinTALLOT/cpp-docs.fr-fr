---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4813'
title: Avertissement du compilateur (niveau 1) C4813
ms.date: 11/04/2016
f1_keywords:
- C4813
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
ms.openlocfilehash: 01c240df7bf9abbee9a9971ec403ff1f3accb1ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255208"
---
# <a name="compiler-warning-level-1-c4813"></a>Avertissement du compilateur (niveau 1) C4813

'function' : une fonction friend d’une classe locale doit avoir été précédemment déclarée

Une fonction friend dans une classe interne n’a pas été déclarée dans la classe externe.

L’exemple suivant génère l’avertissement C4813 :

```cpp
// C4813.cpp
// compile with: /W1 /LD
void MyClass()
{
   // void func();
   class InnerClass
   {
      friend void func();   // C4813 uncomment declaration above
   };
}
```
