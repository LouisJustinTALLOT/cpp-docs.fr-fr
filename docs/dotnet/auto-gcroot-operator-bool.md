---
title: auto_gcroot::operator bool | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_gcroot.operator bool
- auto_gcroot::operator bool
- msclr.auto_gcroot.operator bool
- msclr::auto_gcroot::operator bool
- operator bool
dev_langs: C++
helpviewer_keywords: bool operator
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c327f0ff6e1be74831bb3e0f319ebaf429e7ca70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="autogcrootoperator-bool"></a>auto_gcroot::operator bool
Opérateur pour l’utilisation de `auto_gcroot` dans une expression conditionnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator bool() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si l’objet encapsulé est valide ; `false` dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
 Cet opérateur convertit effectivement en `_detail_class::_safe_bool` qui est plus sûr que `bool` car il ne peut pas être converti en un type intégral.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
```Output  
s is invalid  
now s is valid  
now s is invalid  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [auto_gcroot, membres](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::operator!](../dotnet/auto-gcroot-operator-logical-not.md)