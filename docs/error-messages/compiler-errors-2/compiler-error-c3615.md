---
title: "C3615 d’erreur du compilateur | Documents Microsoft"
ms.date: 10/24/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C3615
dev_langs:
- C++
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea5502ee6e66cf3add4a4ff97e4922a66712ed70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3615"></a>C3615 d’erreur du compilateur

> la fonction constexpr '*fonction*' ne peut pas produire une expression constante

La fonction *fonction* n’a pas pu être évaluée en tant que `constexpr` au moment de la compilation. Pour être `constexpr`, une fonction peut uniquement appeler autres `constexpr` fonctions.

## <a name="example"></a>Exemple

Visual Studio 2017 génère correctement une erreur lors de l’opérande gauche d’une opération de manière conditionnelle l’évaluation n’est pas valide dans un `constexpr` contexte. Le code suivant compile dans Visual Studio 2015, mais pas dans Visual Studio 2017.

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

Pour résoudre ce problème, soit déclarer la `array::size()` fonctionner comme `constexpr` ou supprimer la `constexpr` qualificateur dans `f`.