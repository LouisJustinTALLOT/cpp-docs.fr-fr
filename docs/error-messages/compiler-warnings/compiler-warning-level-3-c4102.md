---
title: Compilateur avertissement (niveau 3) C4102 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4102
dev_langs:
- C++
helpviewer_keywords:
- C4102
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 451fb810da68eb6915203cf087e75371837d16ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082649"
---
# <a name="compiler-warning-level-3-c4102"></a>Avertissement du compilateur (niveau 1) C4102

'label' : étiquette non référencée

L’étiquette est définie mais jamais référencée. Le compilateur ignore l’étiquette.

L’exemple suivant génère l’erreur C4102 :

```
// C4102.cpp
// compile with: /W3
int main() {
   int a;

   test:   // C4102, remove the unreferenced label to resolve

   a = 1;
}
```