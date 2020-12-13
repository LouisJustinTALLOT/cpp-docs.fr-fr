---
description: 'En savoir plus sur : erreur du compilateur C2355'
title: Erreur du compilateur C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: f28799d4fbd72c7a5959bc4c68e1810b26052844
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328376"
---
# <a name="compiler-error-c2355"></a>Erreur du compilateur C2355

'this' : ne peut être référencé qu'à l'intérieur de fonctions membres non static ou d'initialiseurs de données membres non static

Le **`this`** pointeur est valide uniquement dans les fonctions membres non statiques ou dans les initialiseurs de membres de données non statiques. Cette erreur peut intervenir quand la portée de classe d'une définition de fonction membre en dehors de la déclaration de classe n'est pas correctement qualifiée. L’erreur peut également se produire lorsque le **`this`** pointeur est utilisé dans une fonction qui n’est pas déclarée dans la classe.

Pour résoudre ce problème, assurez-vous que la définition de fonction membre correspond à une déclaration de fonction membre dans la classe, et qu'elle n'est pas déclarée static. Pour les initialiseurs de données membres, assurez-vous que les données membres ne sont pas déclarées static.

L'exemple suivant génère l'erreur C2355 et montre comment la corriger :

```cpp
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```
