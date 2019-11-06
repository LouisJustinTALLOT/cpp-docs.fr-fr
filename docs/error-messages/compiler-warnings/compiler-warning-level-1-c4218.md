---
title: Avertissement du compilateur (niveau 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f1db3eabc3b614019676dc4494e83104c62fe579
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627309"
---
# <a name="compiler-warning-level-1-c4218"></a>Avertissement du compilateur (niveau 1) C4218

extension non standard utilisée : vous devez spécifier au moins une classe de stockage ou un type

Avec les extensions Microsoft par défaut (/Ze), vous pouvez déclarer une variable sans spécifier un type ou une classe de stockage. Le type par défaut est `int`.

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