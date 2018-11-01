---
title: Erreur du compilateur C2802
ms.date: 11/04/2016
f1_keywords:
- C2802
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
ms.openlocfilehash: 9024a13b0e4fdbc4174f94e6c0c8736b03f3c221
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538734"
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