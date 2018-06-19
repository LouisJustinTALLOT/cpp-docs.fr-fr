---
title: auto_gcroot::operator! | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr.auto_gcroot.operator!
- auto_gcroot.operator!
- msclr::auto_gcroot::operator!
- auto_gcroot::operator!
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot::operator!
ms.assetid: f9728be3-2e09-4c01-a594-43e0d59d40d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 107ac80f84d949a96132a4fc05c90ad7a7e20fbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103370"
---
# <a name="autogcrootoperator"></a>auto_gcroot::operator!
Opérateur pour l’utilisation de `auto_gcroot` dans une expression conditionnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool operator!() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si l’objet encapsulé n’est pas valide ; `false` dans le cas contraire.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_auto_gcroot_operator_not.cpp  
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
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [auto_gcroot, membres](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::operator bool](../dotnet/auto-gcroot-operator-bool.md)