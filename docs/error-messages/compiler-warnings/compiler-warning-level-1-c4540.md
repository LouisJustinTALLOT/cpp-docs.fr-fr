---
title: Avertissement du compilateur (niveau 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 859ff75bbd4b3fe248d9658495e64c0c039fbb40
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186411"
---
# <a name="compiler-warning-level-1-c4540"></a>Avertissement du compilateur (niveau 1) C4540

dynamic_cast utilisé pour la conversion en base inaccessible ou ambiguë ; le test au moment de l’exécution échoue ('type1 'en’type2 ')

Vous avez utilisé `dynamic_cast` pour convertir un type en un autre. Le compilateur a déterminé que le cast échouait toujours (retourne **null**), car une classe de base est inaccessible (`private`, par exemple) ou ambiguë (apparaît plusieurs fois dans la hiérarchie de classes, par exemple).

L’exemple suivant illustre cet avertissement. La classe **B** est dérivée de **la classe A**. Le programme utilise `dynamic_cast` pour effectuer un cast à partir de la classe **b** (classe dérivée) vers la classe **A**, ce qui échouera toujours, car la classe **b** est `private` et donc inaccessible. La modification de l’accès d' **un** en **public** permet de résoudre l’avertissement.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
