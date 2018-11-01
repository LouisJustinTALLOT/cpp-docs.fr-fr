---
title: Avertissement du compilateur (niveau 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: 4da96fd13fe9ba03c19808d32d3cdd9c73ec2b18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584728"
---
# <a name="compiler-warning-level-1-c4489"></a>Avertissement du compilateur (niveau 1) C4489

'spécificateur' : non autorisé sur la méthode d’interface 'méthode' ; remplacer les spécificateurs sont autorisés uniquement sur les méthodes de classe ref et value

Un mot clé spécificateur a été utilisé incorrectement sur une méthode d’interface.

Pour plus d’informations, consultez [des spécificateurs de substitution](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4489.

```
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```