---
title: Avertissement du compilateur (niveaux 1 et 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 7ce8b3242def187e4b8b442f403f92f013a9ca6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164779"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Avertissement du compilateur (niveaux 1 et 4) C4949

les pragmas’Managed’et’unmanaged’sont significatifs uniquement lorsqu’ils sont compilés avec'/CLR [ : option] '

Le compilateur ignore les pragmas [managés](../../preprocessor/managed-unmanaged.md) et non managés si le code source n’est pas compilé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Cet avertissement est à caractère informatif.

L’exemple suivant génère l’C4949 :

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Quand **#pragma non géré** est utilisé sans **/CLR**, C4949 est un avertissement de niveau 4.

L’exemple suivant génère l’C4949 :

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```
