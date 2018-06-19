---
title: Vector::push_back (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::push_back
dev_langs:
- C++
helpviewer_keywords:
- push_back member [STL/CLR]
ms.assetid: 4a4c302b-e29f-4b68-b759-2f831814d896
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c36668b2f2c4c61a2c4c0047b8a8fb8c9100778f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164607"
---
# <a name="vectorpushback-stlclr"></a>vector::push_back (STL/CLR)
Ajoute un nouvel élément en dernier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void push_back(value_type val);  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre insère un élément avec la valeur `val` à la fin de la séquence contrôlée. Il permet d’ajouter un autre élément dans le vecteur.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)