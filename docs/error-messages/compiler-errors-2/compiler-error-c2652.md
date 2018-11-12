---
title: Erreur du compilateur C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464803"
---
# <a name="compiler-error-c2652"></a>Erreur du compilateur C2652

'identificateur' : constructeur de copie non conforme : premier paramètre ne doit pas être 'identificateur'

Le premier paramètre dans le constructeur de copie a le même type que la classe, de structure ou union pour lequel il est défini. Le premier paramètre peut être une référence au type, mais pas le type lui-même.

L’exemple suivant génère l’erreur C2651 :

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```