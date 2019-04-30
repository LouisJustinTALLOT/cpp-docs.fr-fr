---
title: Erreur du compilateur C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404102"
---
# <a name="compiler-error-c3615"></a>Erreur du compilateur C3615

> la fonction constexpr '*fonction*' ne peut pas produire une expression constante

La fonction *fonction* n’a pas pu être évaluée en tant que `constexpr` au moment de la compilation. Pour être `constexpr`, une fonction peut uniquement appeler autre `constexpr` fonctions.

## <a name="example"></a>Exemple

Visual Studio 2017 génère correctement une erreur lors de l’opérande gauche d’une opération à évaluation conditionnelle n’est pas valide dans un `constexpr` contexte. Le code suivant compile dans Visual Studio 2015, mais pas dans Visual Studio 2017.

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

Pour résoudre ce problème, déclarez le `array::size()` jouer `constexpr` ou supprimer la `constexpr` qualificateur dans `f`.