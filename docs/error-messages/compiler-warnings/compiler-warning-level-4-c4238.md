---
title: Compilateur avertissement (niveau 4) C4238 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057026"
---
# <a name="compiler-warning-level-4-c4238"></a>Avertissement du compilateur (niveau 4) C4238

extension non standard utilisée : classe rvalue utilisée comme lvalue

Pour assurer la compatibilité avec les versions précédentes de Visual C++, les extensions Microsoft (**/Ze**) vous permettent d’utiliser un type de classe comme rvalue dans un contexte qui implicitement ou explicitement prend son adresse. Dans certains cas, comme dans l’exemple ci-dessous, cela peut être dangereux.

## <a name="example"></a>Exemple

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Cette utilisation génère une erreur sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).