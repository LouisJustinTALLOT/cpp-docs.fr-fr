---
title: Erreur du compilateur C2589 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2db5dde898a3e5918eed62b2b32231b5d7ed014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046054"
---
# <a name="compiler-error-c2589"></a>Erreur du compilateur C2589

'identificateur' : jeton non conforme à droite de ' ::'

Si un nom de classe, structure ou union apparaît à gauche de l’opérateur de résolution de portée (double deux-points), le jeton à droite doit être une classe, une structure ou un membre d’union. Sinon, n’importe quel identificateur global peut apparaître sur la droite.

L’opérateur de résolution de portée ne peut pas être surchargé.

L’exemple suivant génère l’erreur C2589 :

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```