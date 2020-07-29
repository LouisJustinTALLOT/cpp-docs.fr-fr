---
title: Avertissement du compilateur (niveau 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 3a89d5c0924e6fd12a4ccf8afa957f8908670d49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223237"
---
# <a name="compiler-warning-level-1-c4228"></a>Avertissement du compilateur (niveau 1) C4228

extension non standard utilisée : les qualificateurs situés après la virgule dans la liste des déclarateurs sont ignorés

L’utilisation de qualificateurs comme **`const`** ou **`volatile`** après une virgule lors de la déclaration de variables est une extension Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Exemple

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
