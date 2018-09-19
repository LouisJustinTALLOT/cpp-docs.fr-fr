---
title: Compilateur avertissement (niveau 1) C4540 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3f553bd1f910c7b17e079dc1f03664c78383e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042765"
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