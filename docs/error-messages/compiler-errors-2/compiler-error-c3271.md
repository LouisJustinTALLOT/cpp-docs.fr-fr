---
title: Erreur du compilateur C3271
ms.date: 11/04/2016
f1_keywords:
- C3271
helpviewer_keywords:
- C3271
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
ms.openlocfilehash: f94ef54408584e40dc406935e36053352ecf38e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365648"
---
# <a name="compiler-error-c3271"></a>Erreur du compilateur C3271

'membre' : valeur 'valeur' non valide pour l’attribut FieldOffset

Un nombre négatif a été passé à l’attribut **FieldOffset** .

L’exemple suivant génère l’erreur C3271 :

```
// C3271.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
value class MyStruct1 {
   public: [FieldOffset(0)] int a;
   public: [FieldOffset(-1)] long b;   // C3271
};
```
