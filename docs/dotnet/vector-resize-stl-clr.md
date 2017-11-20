---
title: Vector::Resize (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::resize
dev_langs: C++
helpviewer_keywords: resize member [STL/CLR]
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43616dbc6bf0cd0eca6493d4f474ce20d02b8e2d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="vectorresize-stlclr"></a>vector::resize (STL/CLR)
Modifie le nombre d’éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Paramètres  
 NEW_SIZE  
 Nouvelle taille de la séquence contrôlée.  
  
 Val  
 Valeur de l’élément de remplissage.  
  
## <a name="remarks"></a>Remarques  
 Les deux fonctions membres Vérifiez que [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` retourne désormais `new_size`. Si elle doit rallonger la séquence contrôlée, la première fonction membre ajoute des éléments avec la valeur `value_type()`, tandis que la deuxième fonction membre ajoute des éléments avec la valeur `val`. Pour rendre la séquence contrôlée plus courte, les deux fonctions membres effacement efficacement le dernier élément [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` fois. Vous l’utilisez pour vous assurer que la séquence contrôlée est de taille `new_size`, par la suppression ou la séquence contrôlée en cours de remplissage.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::Clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)   
 [Vector::Erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)