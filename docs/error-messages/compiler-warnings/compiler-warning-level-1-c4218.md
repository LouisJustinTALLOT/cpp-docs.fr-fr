---
title: Avertissement du compilateur (niveau 4) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 226bc91c272ff62ebe127aa190384d30a214b05d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223250"
---
# <a name="compiler-warning-level-1-c4218"></a>Avertissement du compilateur (niveau 4) C4218

extension non standard utilisée : vous devez spécifier au moins une classe de stockage ou un type

Avec les extensions Microsoft par défaut (/Ze), vous pouvez déclarer une variable sans spécifier un type ou une classe de stockage. Le type par défaut est **`int`** .

## <a name="example"></a>Exemple

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Ces déclarations ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
