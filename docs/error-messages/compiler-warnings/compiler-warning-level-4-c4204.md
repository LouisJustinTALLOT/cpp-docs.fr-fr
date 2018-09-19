---
title: Compilateur avertissement (niveau 4) C4204 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4204
dev_langs:
- C++
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61194e28081c42a71847eca3f97e4d1f46771d16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037539"
---
# <a name="compiler-warning-level-4-c4204"></a>Avertissement du compilateur (niveau 4) C4204

extension non standard utilisée : initialiseur d’agrégat non constant

Avec les extensions Microsoft (/Ze), vous pouvez initialiser des types d’agrégats (tableaux, structures, unions et classes) avec des valeurs qui ne sont pas constantes.

## <a name="example"></a>Exemple

```
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).