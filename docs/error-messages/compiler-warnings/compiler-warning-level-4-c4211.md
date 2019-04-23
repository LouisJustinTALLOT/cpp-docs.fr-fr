---
title: Avertissement du compilateur (niveau 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6d61191c4a7ed950d979158ccdfa3a390439b019
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778304"
---
# <a name="compiler-warning-level-4-c4211"></a>Avertissement du compilateur (niveau 4) C4211

extension non standard utilisée : extern redéfini en static

Avec les extensions Microsoft (/Ze), vous pouvez redéfinir un `extern` identificateur en tant que **statique**.

## <a name="example"></a>Exemple

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Ces redéfinitions ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
