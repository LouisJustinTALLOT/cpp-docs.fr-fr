---
description: En savoir plus sur la recherche de nom de Argument-Dependent (Koenig) sur les fonctions
title: Recherche de nom qui dépend de l’argument (Koenig) sur les fonctions
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 726174041c919a2918687101b223f0e1cca3d5ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288189"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Recherche de nom qui dépend de l’argument (Koenig) sur les fonctions

Le compilateur peut utiliser la recherche de nom dépendante d’un argument pour rechercher la définition d’un appel de fonction non qualifié. La recherche de nom dépendante d'un argument est également appelée recherche Koenig. Le type de chaque argument dans un appel de fonction est défini dans une hiérarchie d’espaces de noms, de classes, de structures, d’unions ou de modèles. Lorsque vous spécifiez un appel de fonction [postfix](../cpp/postfix-expressions.md) non qualifié, le compilateur recherche la définition de fonction dans la hiérarchie associée à chaque type d’argument.

## <a name="example"></a>Exemple

Dans l’exemple, le compilateur note que la fonction `f()` prend un argument `x`. L’argument `x` est de type `A::X`, qui est défini dans l’espace de noms `A`. Le compilateur recherche l'espace de noms `A` et trouve une définition pour la fonction `f()` qui prend un argument de type `A::X`.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```
