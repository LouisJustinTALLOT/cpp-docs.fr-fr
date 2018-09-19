---
title: Compilateur avertissement (niveau 3) C4633 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4633
dev_langs:
- C++
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54a180bcd135f4614fa6cc67cf7647acdfa1c445
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085743"
---
# <a name="compiler-warning-level-3-c4633"></a>Avertissement du compilateur (niveau 3) C4633

Cible de commentaire de document XML : erreur : raison

Un nom passé à la [ \<param >](../../ide/param-visual-cpp.md) balise introuvable par le compilateur.

L’exemple suivant génère l’erreur C4633 :

```
// C4633.cpp
// compile with: /clr /doc /LD /W3

/// Text for class MyClass.
public ref class MyClass {
   // C4633 remove line for Int3
   /// <param name="Int1">Used to indicate status.</param>
   /// <param name="Int3">Used to indicate status.</param>
   void MyMethod(int Int1) {
      Int1 = 0;
      Int1++;
   }
};
```