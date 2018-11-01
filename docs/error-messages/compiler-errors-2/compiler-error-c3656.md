---
title: Erreur du compilateur C3656
ms.date: 11/04/2016
f1_keywords:
- C3656
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
ms.openlocfilehash: 219b8a4135fda963fdce038a75ce0543d6a3433b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465518"
---
# <a name="compiler-error-c3656"></a>Erreur du compilateur C3656

'override' : remplacer spécificateur ne peut pas être répété.

Un mot clé de substitution explicite peut uniquement être spécifié qu’une seule fois. Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3656 :

```
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```