---
title: Recherche de nom dépendante d’un argument (Koenig) sur les fonctions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1977948eae8844b1b8c44310141abaab33b940
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409364"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Recherche de nom qui dépend de l’argument (Koenig) sur les fonctions
Le compilateur peut utiliser la recherche de nom dépendante d’un argument pour rechercher la définition d’un appel de fonction non qualifié. La recherche de nom dépendante d'un argument est également appelée recherche Koenig. Le type de chaque argument dans un appel de fonction est défini dans une hiérarchie d’espaces de noms, de classes, de structures, d’unions ou de modèles. Lorsque vous spécifiez un [suffixés](../cpp/postfix-expressions.md) appel de fonction, le compilateur recherche la définition de fonction dans la hiérarchie associée à chaque type d’argument.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple, le compilateur note que la fonction `f()` prend un argument `x`. L'argument `x` est de type `A::X`, qui est défini dans l'espace de noms `A`. Le compilateur recherche l'espace de noms `A` et trouve une définition pour la fonction `f()` qui prend un argument de type `A::X`.  
  
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