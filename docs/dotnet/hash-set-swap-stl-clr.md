---
title: hash_set::swap (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::swap
dev_langs:
- C++
helpviewer_keywords:
- swap member [STL/CLR]
ms.assetid: 6476e48f-4744-486d-b028-cf0a048acd4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c95c924244fe090e0ccd0ea4cfcbb8a15337e979
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128470"
---
# <a name="hashsetswap-stlclr"></a>hash_set::swap (STL/CLR)
Échange le contenu de deux conteneurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void swap(hash_set<Key>% right);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Conteneur avec lequel échanger le contenu.  
  
## <a name="remarks"></a>Notes  
 La fonction membre échange les séquences contrôlées entre `this` et `right`. Cela se fait en temps constant et ne lève aucune exception. Vous l’utiliser comme un moyen rapide de l’échange le contenu de deux conteneurs.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_hash_set_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_set c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
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
d e f  
d e f  
a b c  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)