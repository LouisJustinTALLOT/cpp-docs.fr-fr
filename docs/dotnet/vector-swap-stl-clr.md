---
title: Vector::swap (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::swap
dev_langs: C++
helpviewer_keywords: swap member [STL/CLR]
ms.assetid: 9ad083fe-f79b-4b97-8013-581fd00c059a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 897f1e2941fd1e3eb6782442aa963f91f70745aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="vectorswap-stlclr"></a>vector::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur avec lequel échanger le contenu.  
  
## <a name="remarks"></a>Remarques  
 La fonction membre échange les séquences contrôlées entre `*this` et `right`. Cela se fait en temps constant et ne lève aucune exception. Vous l’utiliser comme un moyen rapide de l’échange le contenu de deux conteneurs.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_swap.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::vector<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)