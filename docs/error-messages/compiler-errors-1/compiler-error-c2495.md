---
title: Erreur du compilateur C2495 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2495
dev_langs:
- C++
helpviewer_keywords:
- C2495
ms.assetid: bb7066fe-3549-4901-97e4-157f3c04dd57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3425ea527299d9594b1d296a41a4eaec4c3951
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108363"
---
# <a name="compiler-error-c2495"></a>Erreur du compilateur C2495

'identificateur' : 'nothrow' peut uniquement être appliqué aux définitions ou déclarations de fonction

Le [nothrow](../../cpp/nothrow-cpp.md) attribut étendu peut être appliqué aux définitions ou déclarations de fonctions.

L’exemple suivant génère l’erreur C2495 :

```
// C2495.cpp
// compile with: /c
__declspec(nothrow) class X {   // C2495
   int m_data;
} x;

__declspec(nothrow) void test();   // OK
```