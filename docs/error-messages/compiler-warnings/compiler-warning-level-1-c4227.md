---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4227'
title: Avertissement du compilateur (niveau 1) C4227
ms.date: 11/04/2016
f1_keywords:
- C4227
helpviewer_keywords:
- C4227
ms.assetid: 78f98374-c00b-4000-aefa-1b1c67b4666b
ms.openlocfilehash: f919f3765836548b7aa7410002facd942b942395
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266323"
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
