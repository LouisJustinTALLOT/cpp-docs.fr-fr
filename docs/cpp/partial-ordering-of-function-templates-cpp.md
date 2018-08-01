---
title: Classement partiel des modèles de fonction (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75689c07718bf066105920b566087c08a220a7de
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408804"
---
# <a name="partial-ordering-of-function-templates-c"></a>Tri partiel des modèles de fonction (C++)

Plusieurs modèles de fonction qui correspondent à la liste d’arguments d’un appel de fonction peuvent être disponibles. C++ définit un classement partiel des modèles de fonction pour spécifier quelle fonction doit être appelée. Le classement est partiel car certains modèles peuvent être considérés comme également spécialisés.

Le compilateur sélectionne la fonction de modèle la plus spécialisée disponible parmi les correspondances possibles. Par exemple, si un modèle de fonction prend un type __T__et un autre modèle de fonction prenant __T\*__  est disponible, le __T\*__  version est dite pour être plus spécialisée et sont préférée générique __T__ version chaque fois que l’argument est un type pointeur, même si les deux serait autorisées correspondances.

Utilisez le processus suivant pour déterminer si un candidat de modèle de fonction est plus spécialisé :

1. Considérez deux modèles de fonction, T1 et T2.

2. Remplacez les paramètres dans T1 par un type unique hypothétique X.

3. Avec la liste de paramètres dans T1, vérifiez si T2 est un modèle valide pour cette liste de paramètres. Ignorez toutes les conversions implicites.

4. Répétez le même processus en inversant T1 et T2.

5. Si un modèle est une liste d’arguments template valide pour l’autre modèle, mais que l’inverse n’est pas vrai, ce modèle est considéré comme moins spécialisé que l’autre modèle. Si les deux modèles à l’aide des précédente étape formulaire les arguments valides pour eux, puis ils sont considérés comme également spécialisés et entraîne un appel ambigu lorsque vous tentez d’utiliser.

6. Grâce à ces règles :

     1. Une spécialisation de modèle pour un type spécifique est plus spécialisée qu’une spécialisation acceptant un argument de type générique.

     2. Un modèle en prenant uniquement __T\*__  est plus spécialisé qu’un prenant uniquement __T__, car un hypothétique tapez __X\*__  est un argument valid pour un __T__ argument de modèle, mais __X__ n’est pas un argument valide pour un __T\*__  argument template.

     3. __const T__ est plus spécialisé que __T__, car __const X__ est un argument valid pour un __T__ argument de modèle, mais __X__ est argument non valide pour un __const T__ argument template.

     4. __const T\*__  est plus spécialisé que __T\*__, car __const X\*__  est un argument valid pour un __T\*__  argument de modèle, mais __X\*__  n’est pas un argument valide pour un __const T\*__  argument template.

## <a name="example"></a>Exemple

L’exemple suivant fonctionne comme indiqué dans la norme :

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

extern "C" int printf(const char*,...);
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