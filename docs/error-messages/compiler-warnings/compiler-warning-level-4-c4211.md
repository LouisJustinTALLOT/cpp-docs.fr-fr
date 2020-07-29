---
title: Avertissement du compilateur (niveau 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: df19f90e17d6737a2639eb1245da197881e35c96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218102"
---
# <a name="compiler-warning-level-4-c4211"></a>Avertissement du compilateur (niveau 4) C4211

extension non standard utilisée : extern redéfini en static

Avec les extensions Microsoft par défaut (/Ze), vous pouvez redéfinir un **`extern`** identificateur en tant que **`static`** .

## <a name="example"></a>Exemple

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Ces redéfinitions ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
