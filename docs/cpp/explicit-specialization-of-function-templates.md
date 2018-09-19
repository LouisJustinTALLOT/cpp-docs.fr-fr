---
title: Spécialisation explicite des modèles de fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3070108e9e85273a86b93d40301747b658ae231b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029024"
---
# <a name="explicit-specialization-of-function-templates"></a>Spécialisation explicite de modèles de fonctions

Avec un modèle de fonction, vous pouvez définir un comportement spécial pour un type spécifique en fournissant une spécialisation explicite (substitution) du modèle de fonction pour ce type. Exemple :

```cpp
template<> void MySwap(double a, double b);
```

Cette déclaration vous permet de définir une fonction différente pour **double** variables. Comme les fonctions sans modèle, les conversions de type standard (comme la promotion d’une variable de type **float** à **double**) sont appliquées.

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

[Modèles de fonctions](../cpp/function-templates.md)