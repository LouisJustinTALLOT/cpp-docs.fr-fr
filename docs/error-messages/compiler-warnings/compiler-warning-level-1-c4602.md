---
title: Compilateur avertissement (niveau 1) C4602 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
dev_langs:
- C++
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cae5810f94ed9c3feb22de145c7e12e1a7d813b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033314"
---
# <a name="compiler-warning-level-1-c4602"></a>Avertissement du compilateur (niveau 1) C4602

\#pragma pop_macro : 'nom de macro' pas de #pragma push_macro défini au préalable pour cet identificateur

Si vous utilisez [pop_macro](../../preprocessor/pop-macro.md) pour une macro particulière, vous devez au préalable passer le nom de cette macro à [push_macro](../../preprocessor/push-macro.md). L’exemple suivant génère l’avertissement C4602 :

```
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```