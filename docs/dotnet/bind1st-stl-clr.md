---
title: bind1st (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::bind1st
dev_langs:
- C++
helpviewer_keywords:
- bind1st function [STL/CLR]
ms.assetid: 03a04cef-60fb-4667-b22a-22a387adb028
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d602a7422fc9ccc971508b915f6228ffd1659664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105372"
---
# <a name="bind1st-stlclr"></a>bind1st (STL/CLR)
Génère un `binder1st` pour un argument et un functor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
## <a name="template-parameters"></a>Paramètres de modèle  
 Arg  
 Type de l’argument.  
  
 amusement  
 Le type de foncteur.  
  
## <a name="function-parameters"></a>Paramètres de fonction  
 functor  
 La fonction à encapsuler.  
  
 left  
 Le premier argument de retour à la ligne.  
  
## <a name="remarks"></a>Notes  
 La fonction de modèle retourne [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Vous l’utiliser comme un moyen pratique d’encapsuler un functor deux arguments et son premier argument à un functor un argument qui l’appelle avec un deuxième argument.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_bind1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)