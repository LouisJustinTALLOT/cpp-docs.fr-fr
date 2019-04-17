---
title: Erreur du compilateur C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 7394f6b9789caa09ffc2ad6c2cf56f037b5d57b8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767962"
---
# <a name="compiler-error-c3648"></a>Erreur du compilateur C3648

Cette syntaxe de substitution explicite requiert/clr : oldSyntax

Lors de la compilation pour la dernière syntaxe managée, le compilateur a trouvé explicit remplacent la syntaxe pour les versions antérieures ne sont plus pris en charge.

Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3648 :

```
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```