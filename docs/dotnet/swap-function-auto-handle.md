---
title: swap, fonction (auto_handle) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::swap
- msclr.swap
dev_langs:
- C++
helpviewer_keywords:
- swap function
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 66416bf19a154a5ea1f4a52728f97bbfbd3477f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103230"
---
# <a name="swap-function-autohandle"></a>swap, fonction (auto_handle)
Échange les objets entre un `auto_handle` et un autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename _element_type>  
void swap(  
   auto_handle<_element_type> % _left,  
   auto_handle<_element_type> % _right  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*à gauc_he*<br/>
Élément `auto_handle`.  
  
*à d_roite*<br/>
Un autre `auto_handle`.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_swap_auto_handle.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1 = "string one";  
   auto_handle<String> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   swap( s1, s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
```Output  
s1 = 'string one', s2 = 'string two'  
s1 = 'string two', s2 = 'string one'  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [auto_handle](../dotnet/auto-handle.md)   
 [auto_handle::swap](../dotnet/auto-handle-swap.md)