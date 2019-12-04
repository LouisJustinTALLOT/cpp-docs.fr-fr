---
title: Erreur du compilateur C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756121"
---
# <a name="compiler-error-c2652"></a>Erreur du compilateur C2652

'identificateur' : constructeur de copie non conforme : le premier paramètre ne doit pas être un’identificateur'

Le premier paramètre dans le constructeur de copie a le même type que la classe, la structure ou l’Union pour laquelle il est défini. Le premier paramètre peut être une référence au type, mais pas le type lui-même.

L’exemple suivant génère l’C2651 :

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
