---
description: 'En savoir plus sur : erreur du compilateur C2652'
title: Erreur du compilateur C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 6d0f85a089c527ce299e007ce04d96ac68daaf56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286174"
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
