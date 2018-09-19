---
title: Erreur du compilateur C2355 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 456049c60ce39fce3cdbf04512f306027e30db25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035186"
---
# <a name="compiler-error-c2355"></a>Erreur du compilateur C2355

'this' : ne peut être référencé qu'à l'intérieur de fonctions membres non static ou d'initialiseurs de données membres non static

Le pointeur `this` est valide uniquement à l'intérieur de fonctions membres non static ou d'initialiseurs de données membres non static. Cette erreur peut intervenir quand la portée de classe d'une définition de fonction membre en dehors de la déclaration de classe n'est pas correctement qualifiée. L'erreur peut également se produire quand le pointeur `this` est utilisé dans une fonction qui n'est pas déclarée dans la classe.

Pour résoudre ce problème, assurez-vous que la définition de fonction membre correspond à une déclaration de fonction membre dans la classe, et qu'elle n'est pas déclarée static. Pour les initialiseurs de données membres, assurez-vous que les données membres ne sont pas déclarées static.

L'exemple suivant génère l'erreur C2355 et montre comment la corriger :

```
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