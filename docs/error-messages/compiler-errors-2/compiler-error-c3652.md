---
title: Erreur du compilateur C3652
ms.date: 11/04/2016
f1_keywords:
- C3652
helpviewer_keywords:
- C3652
ms.assetid: 15d68737-177e-41f1-80e0-7c3e2afdf0fc
ms.openlocfilehash: 350edcf409cf2a890a8f83147ce0ae13e9992694
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777614"
---
# <a name="compiler-error-c3652"></a>Erreur du compilateur C3652

'override' : une fonction de substitution explicite doit être virtuelle

Une fonction qui effectue une substitution explicite doit être virtuelle. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3652 :

```
// C3652.cpp
// compile with: /clr /c
public interface class I {
   void f();
};

public ref struct R : I {
   void f() = I::f {}   // C3652
   // try the following line instead
   // virtual void f() = I::f {}
};
```