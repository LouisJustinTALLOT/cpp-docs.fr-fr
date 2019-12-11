---
title: Avertissement du compilateur (niveau 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: cc913a4f92963437347fbc708eca03c25ab9d403
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991467"
---
# <a name="compiler-warning-level-4-c4238"></a>Avertissement du compilateur (niveau 4) C4238

extension non standard utilisée : classe rvalue utilisée comme lvalue

Pour la compatibilité avec les versions précédentes C++de Visual, les extensions Microsoft ( **/Ze**) vous permettent d’utiliser un type de classe comme rvalue dans un contexte qui prend implicitement ou explicitement son adresse. Dans certains cas, comme dans l’exemple ci-dessous, cela peut être dangereux.

## <a name="example"></a>Exemple

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Cette utilisation provoque une erreur sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
