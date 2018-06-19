---
title: moins (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::minus
dev_langs:
- C++
helpviewer_keywords:
- minus function [STL/CLR]
ms.assetid: 810ec6fd-ed0e-446b-b18e-1e612fb1fff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 655dda0dc23b603e06870ff9f70941fb5156a1cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134515"
---
# <a name="minus-stlclr"></a>minus (STL/CLR)
La classe de modèle décrit un functor qui, lorsqu’elle est appelée, retourne le premier argument moins le second. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class minus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    minus();  
    minus(minus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments et de la valeur de retour.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|delegate_type|Le type du délégué générique.|  
|first_argument_type|Le type du premier argument functor.|  
|RESULT_TYPE|Le type du résultat functor.|  
|second_argument_type|Le type du second argument functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|minus|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor deux arguments. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne le premier argument, moins la seconde.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_minus.cpp   
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
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::minus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
2 2  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [plus (STL/CLR)](../dotnet/plus-stl-clr.md)