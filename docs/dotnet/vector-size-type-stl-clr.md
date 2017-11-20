---
title: Vector::size_type (STL/CLR) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::size_type
dev_langs: C++
helpviewer_keywords: size_type member [STL/CLR]
ms.assetid: 0789e887-e79a-42f9-a162-fc27f1341900
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31e464d1880847751e1134c226b0964654270ee5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="vectorsizetype-stlclr"></a>vector::size_type (STL/CLR)
Type d'une distance signée entre deux éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef int size_type;  
```  
  
## <a name="remarks"></a>Remarques  
 Le type décrit un nombre non négatif élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_size_type.cpp   
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
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)