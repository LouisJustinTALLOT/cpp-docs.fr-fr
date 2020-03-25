---
title: Avertissement du compilateur (niveau 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173918"
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
