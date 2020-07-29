---
title: Avertissement du compilateur (niveau 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: 0b590eaef2094c3d1c3a83541e9d5e10415928f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223211"
---
# <a name="compiler-warning-level-1-c4230"></a>Avertissement du compilateur (niveau 1) C4230

anachronisme utilisé : modificateurs/qualificateurs parsemés ; qualificateur ignoré

L’utilisation d’un qualificateur avant un modificateur Microsoft comme **`__cdecl`** est une pratique obsolète.

## <a name="example"></a>Exemple

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
