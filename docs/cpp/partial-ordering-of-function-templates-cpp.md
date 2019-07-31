---
title: Tri partiel des modèles de fonction (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682426"
---
# <a name="partial-ordering-of-function-templates-c"></a>Tri partiel des modèles de fonction (C++)

Plusieurs modèles de fonction qui correspondent à la liste d’arguments d’un appel de fonction peuvent être disponibles. C++ définit un classement partiel des modèles de fonction pour spécifier quelle fonction doit être appelée. Le classement est partiel car certains modèles peuvent être considérés comme également spécialisés.

Le compilateur sélectionne la fonction de modèle la plus spécialisée disponible parmi les correspondances possibles. Par exemple, si un modèle de fonction prend un `T` type et qu’un autre modèle `T*` de fonction qui prend `T*` est disponible, la version est dite plus spécialisée. Il est préférable d’utiliser la `T` version générique chaque fois que l’argument est un type pointeur, même si les deux sont des correspondances autorisées.

Utilisez le processus suivant pour déterminer si un candidat de modèle de fonction est plus spécialisé :

1. Considérez deux modèles de fonction, T1 et T2.

1. Remplacez les paramètres dans T1 par un type unique hypothétique X.

1. Avec la liste de paramètres dans T1, vérifiez si T2 est un modèle valide pour cette liste de paramètres. Ignorez toutes les conversions implicites.

1. Répétez le même processus en inversant T1 et T2.

1. Si un modèle est une liste d’arguments template valide pour l’autre modèle, mais que l’inverse n’est pas vrai, ce modèle est considéré comme moins spécialisé que l’autre modèle. Si, à l’aide de l’étape précédente, les deux modèles forment des arguments valides l’un pour l’autre, ils sont considérés comme étant également spécialisés et un appel ambigu se produit lorsque vous tentez de les utiliser.

1. Grâce à ces règles :

   1. Une spécialisation de modèle pour un type spécifique est plus spécialisée qu'une spécialisation acceptant un argument de type générique.

   1. Un modèle acceptant `T*` uniquement est plus spécialisé qu’un modèle `T`acceptant uniquement, car `X*` un type hypothétique est un argument `T` valide pour un argument `X` template, mais n’est pas un argument valide pour un `T*`argument template.

   1. `const T`est plus spécialisé que `T`, car `const X` est un argument valide pour un `T` argument de modèle, `X` mais n’est pas un argument valide `const T` pour un argument de modèle.

   1. `const T*`est plus spécialisé que `T*`, car `const X*` est un argument valide pour un `T*` argument de modèle, `X*` mais n’est pas un argument valide `const T*` pour un argument de modèle.

## <a name="example"></a>Exemples

L’exemple suivant fonctionne comme indiqué dans la norme:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Sortie

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>Voir aussi

[Modèles de fonctions](../cpp/function-templates.md)
