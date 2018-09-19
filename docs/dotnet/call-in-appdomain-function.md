---
title: call_in_appdomain, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- call_in_appdomain
dev_langs:
- C++
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 707ee9476ce26de9325337f6f2130e41d19faa3a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105243"
---
# <a name="callinappdomain-function"></a>call_in_appdomain, fonction
Exécute une fonction dans un domaine d’application spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename ArgType1, ...typename ArgTypeN>  
void call_in_appdomain(  
   DWORD appdomainId,  
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,  
   ArgType1 arg1,  
   ...  
   ArgTypeN argN ]  
);  
template <typename RetType, typename ArgType1, ...typename ArgTypeN>  
RetType call_in_appdomain(  
   DWORD appdomainId,  
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,  
   ArgType1 arg1,  
   ...  
   ArgTypeN argN ]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*appdomainId*<br/>
Appdomain dans lequel appeler la fonction.  
  
*voidFunc*<br/>
Pointeur vers un `void` fonction qui accepte des paramètres de N (0 < = N < = 15).  
  
*nonvoidFunc*<br/>
Pointeur vers non -`void` fonction qui accepte des paramètres de N (0 < = N < = 15).  
  
*Arg1... argN*<br/>
Zéro à 15 paramètres à passer à `voidFunc` ou `nonvoidFunc` dans l’autre appdomain.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat de l’exécution `voidFunc` ou `nonvoidFunc` dans le domaine d’application spécifié.  
  
## <a name="remarks"></a>Notes  
 Les arguments de la fonction passé à `call_in_appdomain` ne doit pas être de types CLR.  
  
## <a name="example"></a>Exemple  
  
```  
// msl_call_in_appdomain.cpp  
// compile with: /clr  
  
// Defines two functions: one takes a parameter and returns nothing,  
// the other takes no parameters and returns an int.  Calls both  
// functions in the default appdomain and in a newly-created  
// application domain using call_in_appdomain.  
  
#include <msclr\appdomain.h>  
  
using namespace System;  
using namespace msclr;  
  
void PrintCurrentDomainName( char* format )  
{  
   String^ s = gcnew String(format);  
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );  
}  
  
int GetDomainId()  
{  
   return AppDomain::CurrentDomain->Id;  
}  
  
int main()  
{  
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );  
  
   call_in_appdomain( AppDomain::CurrentDomain->Id,  
                   &PrintCurrentDomainName,  
                   (char*)"default appdomain: {0}" );  
   call_in_appdomain( appDomain1->Id,  
                   &PrintCurrentDomainName,  
                   (char*)"in appDomain1: {0}" );  
  
   int id;  
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );  
   Console::WriteLine( "default appdomain id = {0}", id );  
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );  
   Console::WriteLine( "appDomain1 id = {0}", id );  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
default appdomain: msl_call_in_appdomain.exe  
in appDomain1: First Domain  
default appdomain id = 1  
appDomain1 id = 2  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Fichier d’en-tête** \<msclr\appdomain.h >  
  
 **Namespace** msclr