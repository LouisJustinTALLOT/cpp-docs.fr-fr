---
title: unary_negate (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- unary_negate function [STL/CLR]
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 70ce2872e3e941df11402ccde0cb7a94b132b51c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169447"
---
# <a name="unarynegate-stlclr"></a>unary_negate (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne la logique pas de son stockée functor d’un argument. Vous l’utilisez spécifier un objet de fonction en termes de son functor stockée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 amusement  
 Le type de la fonction stockée.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|argument_type|Le type de l’argument functor.|  
|delegate_type|Le type du délégué générique.|  
|RESULT_TYPE|Le type du résultat functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|unary_negate|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument qui stocke un autre un argument functor. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne la logique pas de la fonction stockée appelée avec l’argument.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [not1 (STL/CLR)](../dotnet/not1-stl-clr.md)