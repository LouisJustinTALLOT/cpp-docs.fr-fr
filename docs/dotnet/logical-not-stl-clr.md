---
title: logical_not (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not function [STL/CLR]
ms.assetid: 32a2c6e2-1c58-41ac-8827-f3ee5adfe81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4048c642a1c562237bccba8fa3e5fd5429bba4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134227"
---
# <a name="logicalnot-stlclr"></a>logical_not (STL/CLR)
La classe de modèle décrit un functor que, lorsqu’elle est appelée, retourne true uniquement si son argument teste comme false. Vous l’utilisez spécifier un objet de fonction en termes de son type d’argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Le type des arguments.  
  
## <a name="member-functions"></a>Fonctions membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|argument_type|Le type de l’argument functor.|  
|delegate_type|Le type du délégué générique.|  
|RESULT_TYPE|Le type du résultat functor.|  
  
|Membre|Description|  
|------------|-----------------|  
|logical_not|Construit le foncteur.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|operator()|Calcule la fonction de votre choix.|  
|opérateur delegate_type ^|Effectue un cast de la fonction d’un délégué.|  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un functor un argument. Il définit l’opérateur membre `operator()` , afin que, lorsque l’objet est appelée en tant que fonction, elle retourne true uniquement si son argument tests comme false.  
  
 Vous pouvez également passer l’objet comme un argument de fonction dont le type est `delegate_type^` et il sera converti en conséquence.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_logical_not.cpp   
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
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
0 1  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [negate (STL/CLR)](../dotnet/negate-stl-clr.md)