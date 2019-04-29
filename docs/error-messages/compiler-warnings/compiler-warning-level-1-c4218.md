---
title: Avertissement du compilateur (niveau 4) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 36d5de3b1270b41edfc391df960a556aca207709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386471"
---
# <a name="compiler-warning-level-1-c4218"></a>Avertissement du compilateur (niveau 4) C4218

extension non standard utilisée : doit spécifier au moins une classe de stockage ou d’un type

Avec les extensions Microsoft (/Ze), vous pouvez déclarer une variable sans spécification d’une classe de type ou de stockage. Le type par défaut est `int`.

## <a name="example"></a>Exemple

```
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Ces déclarations sont non valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).