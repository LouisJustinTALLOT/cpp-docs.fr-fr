---
title: Compilateur avertissement (niveau 1) C4489 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4489
dev_langs:
- C++
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc019c618a5e4b8a453652573f6f407279792d56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023252"
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