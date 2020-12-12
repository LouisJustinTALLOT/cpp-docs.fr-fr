---
description: 'En savoir plus sur : erreur du compilateur C3615'
title: Erreur du compilateur C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: 9f3b95b96ff10a99f3ebeac1bc3b19f759dd0ab7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262280"
---
# <a name="compiler-error-c3615"></a>Erreur du compilateur C3615

> la fonction constexpr'*Function*'ne peut pas produire une expression constante

La *fonction* de fonction n’a pas pu être évaluée comme **`constexpr`** au moment de la compilation. Pour être **`constexpr`** , une fonction peut uniquement appeler d’autres **`constexpr`** fonctions.

## <a name="example"></a>Exemple

Visual Studio 2017 génère correctement une erreur lorsque l’opérande gauche d’une opération d’évaluation conditionnelle n’est pas valide dans un **`constexpr`** contexte. Le code suivant se compile dans Visual Studio 2015, mais pas dans Visual Studio 2017.

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

Pour résoudre ce problème, déclarez la `array::size()` fonction comme **`constexpr`** ou supprimez le **`constexpr`** qualificateur de `f` .
