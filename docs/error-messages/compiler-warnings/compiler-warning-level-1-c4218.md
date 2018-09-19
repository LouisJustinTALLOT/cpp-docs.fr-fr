---
title: Compilateur avertissement (niveau 1) C4218 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1970dd1bd231716f59508a7cca9f82d3e13151ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074043"
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