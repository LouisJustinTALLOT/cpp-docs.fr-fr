---
description: 'En savoir plus sur : spécialisation explicite des modèles de fonction'
title: Spécialisation explicite de modèles de fonctions
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: c77ebce3383ba2051ac010c39a7dd0eb37b8111a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181499"
---
# <a name="explicit-specialization-of-function-templates"></a>Spécialisation explicite de modèles de fonctions

Avec un modèle de fonction, vous pouvez définir un comportement spécial pour un type spécifique en fournissant une spécialisation explicite (substitution) du modèle de fonction pour ce type. Par exemple :

```cpp
template<> void MySwap(double a, double b);
```

Cette déclaration vous permet de définir une fonction différente pour les **`double`** variables. À l’instar des fonctions non basées sur les modèles, les conversions de type standard (telles que la promotion d’une variable de type **`float`** en **`double`** ) sont appliquées.

## <a name="example"></a>Exemple

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Modèles de fonction](../cpp/function-templates.md)
