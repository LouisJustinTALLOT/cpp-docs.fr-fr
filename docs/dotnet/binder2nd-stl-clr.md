---
title: binder2nd (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::binder2nd
dev_langs:
- C++
helpviewer_keywords:
- binder2nd function [STL/CLR]
ms.assetid: f4be8722-1778-4cb9-9ec7-ad1443f6899f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d203463213f970d70758ef69ab398f12a52c422f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107842"
---
# <a name="binder2nd-stlclr"></a>binder2nd (STL/CLR)
La classe de modèle décrit un functor un argument qui, lorsqu’elle est appelée, retourne sa functor deux arguments stockée appelé avec le premier argument fourni et son deuxième argument stockée. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
|stored_function_type|Le type de foncteur.|  
  
|Membre|Description|  
|------------|-----------------|  
|binder2nd|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument qui stocke un functor deux arguments et un deuxième argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le résultat de l’appel de la fonction stockée avec le premier argument fourni et le deuxième argument stocké.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_binder2nd.cpp   
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
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)