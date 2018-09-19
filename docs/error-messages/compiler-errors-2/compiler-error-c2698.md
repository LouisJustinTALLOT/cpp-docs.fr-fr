---
title: Erreur du compilateur C2698 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7ca3e7568640aabd2b7960d97ea94a11a1d5d59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118919"
---
# <a name="compiler-error-c2698"></a>Erreur du compilateur C2698

la déclaration using pour ' déclaration 1' ne peuvent pas coexister avec la déclaration using existante pour ' déclaration 2'

Une fois que vous avez un [à l’aide de la déclaration](../../cpp/using-declaration.md) pour un membre de données, à l’aide de n’importe quel déclaration dans la même portée qui utilise le même nom n’est pas autorisée, car seules les fonctions peuvent être surchargées.

L’exemple suivant génère C2698 :

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```