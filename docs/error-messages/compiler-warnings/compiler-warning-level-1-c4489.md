---
title: Avertissement du compilateur (niveau 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: 78ceecb5918ccb74bd61afe62bbf8b542d585f81
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966195"
---
# <a name="compiler-warning-level-1-c4489"></a>Avertissement du compilateur (niveau 1) C4489

'specifier' : non autorisé sur la méthode d’interface’méthode'; les spécificateurs de substitution sont uniquement autorisés sur les méthodes de classe ref et de classe value

Un mot clé de spécificateur a été incorrectement utilisé sur une méthode d’interface.

Pour plus d’informations, consultez [spécificateurs de substitution](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4489.

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```