---
title: Avertissement du compilateur (niveau 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: 6081acc4a64394c9122650da8b7f4147f724e5de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219922"
---
# <a name="compiler-warning-level-4-c4232"></a>Avertissement du compilateur (niveau 4) C4232

extension non standard utilisée : 'identifier' : adresse de DllImport’DllImport’non static, identité non garantie

Sous les extensions Microsoft (/Ze), vous pouvez attribuer une valeur non statique à l’adresse d’une fonction déclarée avec le **`dllimport`** modificateur. Sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), cela provoque une erreur.

L’exemple suivant génère l’C4232 :

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
