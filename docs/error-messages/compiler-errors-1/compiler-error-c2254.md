---
title: Erreur du compilateur C2254 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2254
dev_langs:
- C++
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6030f85ef1b8742b07f1be92101d740732207fa5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067088"
---
# <a name="compiler-error-c2254"></a>Erreur du compilateur C2254

'fonction' : spécificateur pure ou substitution abstrait spécificateur non autorisé sur une fonction friend

Un `friend` (fonction) est spécifiée comme pure `virtual`.

L’exemple suivant génère C2254 :

```
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```