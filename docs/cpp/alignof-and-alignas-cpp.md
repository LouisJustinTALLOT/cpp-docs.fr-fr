---
title: alignof et alignas (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2988d1260cac91e2614765aba8ae1b9be9b922
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407981"
---
# <a name="alignof-and-alignas-c"></a>alignof et alignas (C++)
Le spécificateur de type `alignas` est un élément standard C++ portable qui permet de spécifier un alignement personnalisé des variables et des types définis par l'utilisateur. L'opérateur `alignof` est également un élément standard portable permettant d'obtenir l'alignement d'une variable ou d'un type spécifié.  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser `alignas` sur une classe, un struck ou une union, ou sur des membres individuels. Quand plusieurs spécificateurs `alignas` sont utilisés, le compilateur choisit celui qui est le plus strict (celui ayant la plus grande valeur).  
  
```cpp  
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar  
{      
    int i;       // 4 bytes  
    int n;      // 4 bytes  
    alignas(4) char arr[3];  
    short s;          // 2 bytes  
};  

int main()
{  
    std::cout << alignof(Bar) << std::endl; // output: 16  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Alignement](../cpp/alignment-cpp-declarations.md)