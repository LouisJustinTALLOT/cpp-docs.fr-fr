---
title: equal_to (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::equal_to
dev_langs:
- C++
helpviewer_keywords:
- equal_to function [STL/CLR]
ms.assetid: 9dd6e27d-e695-470f-b7a7-19a6db970ee5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 492398ab8d82b7b97a4116766d7b1e98be525aae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108499"
---
# <a name="equalto-stlclr"></a>equal_to (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si le premier argument est égal au second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    equal_to();  
    equal_to(equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|equal_to|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type^()|Effectue un cast de la fonction d’un délégué.|  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, il retourne true uniquement si le premier argument est égal au second.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_equal_to.cpp   
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
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
1 0  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)