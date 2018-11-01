---
title: Avertissement du compilateur (niveau 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473669"
---
# <a name="compiler-warning-level-1-c4540"></a>Avertissement du compilateur (niveau 1) C4540

utilisé de dynamic_cast pour convertir une base ambiguë ou inaccessible ; test d’exécution échouera ('type1' en 'type2')

Vous avez utilisé `dynamic_cast` pour convertir un type en un autre. Le compilateur a déterminé que le cast échoue toujours (retourner **NULL**) parce qu’une classe de base est inaccessible (`private`, par exemple) ou ambiguë (apparaît plusieurs fois dans la hiérarchie de classes, par exemple).

Voici un exemple de cet avertissement. Classe **B** est dérivé de la classe **A**. Le programme utilise `dynamic_cast` pour effectuer un cast à partir de la classe **B** (la classe dérivée) à la classe **A**, qui échoue toujours, car classe **B** est `private` et par conséquent inaccessible. Modification d’accès de **A** à **public** résout l’avertissement.

```
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