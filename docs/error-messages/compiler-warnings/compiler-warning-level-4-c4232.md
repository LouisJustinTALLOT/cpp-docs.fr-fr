---
title: Avertissement du compilateur (niveau 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: dee087b73bf032a68daf0527ea584efcc7579361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401083"
---
# <a name="compiler-warning-level-4-c4232"></a>Avertissement du compilateur (niveau 4) C4232

extension non standard utilisée : 'identificateur' : adresse de dllimport 'dllimport' n’est pas statique, identité non garantie

Sous les extensions Microsoft (/Ze), vous pouvez donner une valeur non statique comme l’adresse d’une fonction déclarée avec le **dllimport** modificateur. Sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), cela provoque une erreur.

L’exemple suivant génère l’erreur C4232 :

```
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```