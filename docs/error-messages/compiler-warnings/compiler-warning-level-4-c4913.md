---
title: Compilateur avertissement (niveau 4) C4913 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4913
dev_langs:
- C++
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2567659b4fee80a7e620bfbe29a4fba78c3aad44
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041907"
---
# <a name="compiler-warning-level-4-c4913"></a>Avertissement du compilateur (niveau 4) C4913

**l'opérateur binaire défini par l'utilisateur ',' existe mais aucune surcharge n'a pu convertir tous les opérandes, opérateur binaire intégré par défaut ',' utilisé**

Un appel à l’opérateur virgule intégré s’est produit dans un programme où figure également un opérateur virgule surchargé. Une conversion censée être terminée n’a pas été effectuée.

Le code suivant génère l’avertissement C4913 :

```
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```