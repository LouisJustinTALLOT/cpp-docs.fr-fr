---
title: Avertissement du compilateur (niveau 4) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: a45cd6cf86eb8ab1edb33ad5e0df8374972c425e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386484"
---
# <a name="compiler-warning-level-1-c4215"></a>Avertissement du compilateur (niveau 4) C4215

extension non standard utilisée : long float

Les extensions Microsoft (/Ze) traitent **long float** comme **double**. La compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ne le fait pas. Utilisez **double** pour assurer la compatibilité.

L’exemple suivant génère l’erreur C4215 :

```
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```