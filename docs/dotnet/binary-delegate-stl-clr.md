---
title: binary_delegate (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::binary_delegate
dev_langs:
- C++
helpviewer_keywords:
- binary_delegate function [STL/CLR]
ms.assetid: 52a9291a-e354-4b9e-a035-78dac1179ec5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cdca27b416f8e721a44b475d115ac902696b4a85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105762"
---
# <a name="binarydelegate-stlclr"></a>binary_delegate (STL/CLR)
La classe genereic décrit un délégué à deux arguments. Vous l’utilisez spécifier en termes de ses types d’arguments et de retour d’un délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Paramètres  
 arg1  
 Le type du premier argument.  
  
 Arg2  
 Le type du second argument.  
  
 Résultat  
 Type de retour.  
  
## <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction de deux arguments.  
  
 Notez que pour :  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 ils ne sont pas du même type.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)   
 [unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)