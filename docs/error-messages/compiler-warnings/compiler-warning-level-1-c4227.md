---
title: Avertissement du compilateur (niveau 1) C4227
ms.date: 11/04/2016
f1_keywords:
- C4227
helpviewer_keywords:
- C4227
ms.assetid: 78f98374-c00b-4000-aefa-1b1c67b4666b
ms.openlocfilehash: f5cc9e67c06443a73692ce663a2106dacff6035c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221014"
---
# <a name="compiler-warning-level-1-c4227"></a>Avertissement du compilateur (niveau 1) C4227

anachronisme utilisé : les qualificateurs sur la référence sont ignorés

L’utilisation de qualificateurs comme **`const`** ou **`volatile`** avec des références C++ est une pratique obsolète.

## <a name="example"></a>Exemple

```cpp
// C4227.cpp
// compile with: /W1 /c
int j = 0;
int &const i = j;   // C4227
```
