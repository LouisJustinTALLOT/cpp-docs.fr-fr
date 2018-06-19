---
title: opérateur ! = (vecteur) (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::operator!=
dev_langs:
- C++
helpviewer_keywords:
- operator!= member [STL/CLR]
ms.assetid: 6f7b0569-b2d1-4f36-8520-31839bf6db9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de581c52362faf0fb9583d79238f3bb0974d0d26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139643"
---
# <a name="operator-vector-stlclr"></a>operator!= (vector) (STL/CLR)
Vecteur de comparaison n’est pas égal.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    bool operator!=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 left  
 Conteneur de gauche à comparer.  
  
 droite  
 Conteneur de droite à comparer.  
  
## <a name="remarks"></a>Notes  
 La fonction d’opérateur retourne `!(left == right)`. Il permet de tester si `left` n’est pas ordonné identique `right` lorsque les deux vecteurs sont comparé élément par élément.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_operator_ne.cpp   
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
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [opérateur == (vecteur) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)   
 [opérateur\< (vecteur) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [opérateur > = (vecteur) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)   
 [opérateur > (vecteur) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)   
 [operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)