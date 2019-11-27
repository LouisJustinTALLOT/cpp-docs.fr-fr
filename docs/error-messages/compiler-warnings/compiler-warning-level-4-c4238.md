---
title: Avertissement du compilateur (niveau 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 982457ded987f6aee4f2891bbb7d9103b830cc99
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541788"
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