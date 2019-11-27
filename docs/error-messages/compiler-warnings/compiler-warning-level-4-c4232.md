---
title: Avertissement du compilateur (niveau 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: 9d328b1b5e4c3875f29b48eab77cd6f6d49d447f
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541890"
---
# <a name="compiler-warning-level-4-c4232"></a>Avertissement du compilateur (niveau 4) C4232

extension non standard utilisée : 'identifier' : adresse de DllImport’DllImport’non static, identité non garantie

Sous les extensions Microsoft (/Ze), vous pouvez attribuer une valeur non statique à l’adresse d’une fonction déclarée avec le modificateur **DllImport** . Sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), cela provoque une erreur.

L’exemple suivant génère l’C4232 :

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```