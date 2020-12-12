---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4218'
title: Avertissement du compilateur (niveau 4) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 76fc53a5b290a55c73fe036e2fc02b7a1afedd23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266414"
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
