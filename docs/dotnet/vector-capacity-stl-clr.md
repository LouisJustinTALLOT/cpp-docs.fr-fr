---
title: Vector::Capacity (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::capacity
dev_langs:
- C++
helpviewer_keywords:
- capacity member [STL/CLR]
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9a08766c6b23deb4e36ad8c83f9c1f3e2bc1df1f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167565"
---
# <a name="vectorcapacity-stlclr"></a>vector::capacity (STL/CLR)
Indique la taille de stockage alloué pour le conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_type capacity();  
```  
  
## <a name="remarks"></a>Notes  
 La fonction membre retourne le stockage actuellement alloué pour la séquence contrôlée, une valeur au moins aussi grande que [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Il permet de déterminer la quantité le conteneur peut croître avant qu’il doit réallouer le stockage pour la séquence contrôlée.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  
  
## <a name="description"></a>Description  
 Notez que la capacité réelle peut différer les valeurs indiquées ici, aussi longtemps que tous les `ok` signalent la valeur true.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)