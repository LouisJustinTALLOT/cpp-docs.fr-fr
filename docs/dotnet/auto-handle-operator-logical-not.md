---
title: auto_handle::operator! | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr.auto_handle.operator!
- msclr::auto_handle::operator!
- auto_handle.operator!
- auto_handle::operator!
dev_langs:
- C++
helpviewer_keywords:
- operator!
ms.assetid: 3f6c7729-3260-4842-87f9-c491c140b299
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0e4ea5e5bc074795c48eaf63605e623c455dc69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102769"
---
# <a name="autohandleoperator"></a>auto_handle::operator!
Opérateur pour l’utilisation de `auto_handle` dans une expression conditionnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool operator!();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si l’objet encapsulé n’est pas valide ; `false` dans le cas contraire.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_auto_handle_operator_not.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "something";  
   if ( s1) Console::WriteLine( "s1 is valid" );  
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );  
   if ( s2 ) Console::WriteLine( "s2 is valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );  
   s2.reset();  
   if ( s2 ) Console::WriteLine( "s2 is now valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );  
}  
```  
  
```Output  
s1 is invalid  
s2 is valid  
s2 is now invalid  
```  
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [auto_handle, membres](../dotnet/auto-handle-members.md)   
 [auto_handle::operator bool](../dotnet/auto-handle-operator-bool.md)