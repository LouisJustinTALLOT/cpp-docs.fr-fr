---
title: Erreur du compilateur C2802 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2802
dev_langs:
- C++
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95b4f64aad9cb14151ca6128bedebcd15ece17ed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061251"
---
# <a name="compiler-error-c2802"></a>Erreur du compilateur C2802

un membre static 'operator opérateur' n’a aucun paramètre formel

Un opérateur déclaré par une `static` fonction membre doit avoir au moins un paramètre.

L’exemple suivant génère C2802 :

```
// C2802.cpp
// compile with: /clr /c
ref class A {
   static operator+ ();   // C2802
   static operator+ (A^, A^);   // OK
};
```