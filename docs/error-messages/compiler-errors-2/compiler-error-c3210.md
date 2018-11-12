---
title: Erreur du compilateur C3210
ms.date: 11/04/2016
f1_keywords:
- C3210
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
ms.openlocfilehash: 9e0ac1aded7eef40be0e923b3ac1ebc9ef00c7a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528737"
---
# <a name="compiler-error-c3210"></a>Erreur du compilateur C3210

'type' : déclaration d’accès peut uniquement être appliquée à un membre de classe de base

Un [à l’aide de la déclaration](../../cpp/using-declaration.md) a été spécifié de manière incorrecte.

## <a name="example"></a>Exemple

L’exemple suivant génère C3210.

```
// C3210.cpp
// compile with: /c
struct A {
protected:
   int i;
};

struct B {
   using A::i;   // C3210
};

struct C : public A {
   using A::i;   // OK
};
```