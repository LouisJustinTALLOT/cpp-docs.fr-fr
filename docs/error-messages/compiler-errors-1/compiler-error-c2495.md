---
title: Erreur du compilateur C2495
ms.date: 11/04/2016
f1_keywords:
- C2495
helpviewer_keywords:
- C2495
ms.assetid: bb7066fe-3549-4901-97e4-157f3c04dd57
ms.openlocfilehash: 83a0359fce175b12dd18e2500d63d7a86bed9f0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360851"
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