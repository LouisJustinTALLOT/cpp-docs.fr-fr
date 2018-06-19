---
title: unary_delegate (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::unary_delegate
dev_langs:
- C++
helpviewer_keywords:
- unary_delegate function [STL/CLR]
ms.assetid: b3ee253c-98e8-466e-a272-505e47aed061
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 689fc3afba26d4b20816f3513262b6c1fc269e2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167331"
---
# <a name="unarydelegate-stlclr"></a>unary_delegate (STL/CLR)
La classe genereic décrit un délégué à un argument. Vous l’utilisez spécifier en termes de ses types d’arguments et de retour d’un délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
generic<typename Arg,  
    typename Result>  
    delegate Result unary_delegate(Arg);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Arg  
 Type de l'argument.  
  
 Résultat  
 Type de retour.  
  
## <a name="remarks"></a>Notes  
 Le délégué genereic décrit une fonction d’un argument.  
  
 Notez que pour :  
  
 `unary_delegare<int, int> Fun1;`  
  
 `unary_delegare<int, int> Fun2;`  
  
 les types `Fun1` et `Fun2` sont des synonymes, tandis que pour :  
  
 `delegate int Fun1(int);`  
  
 `delegate int Fun2(int);`  
  
 ils ne sont pas du même type.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_unary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
int hash_val(wchar_t val)   
    {   
    return ((val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate<wchar_t, int> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 5  
hash(L'b') = 22  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)   
 [binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)