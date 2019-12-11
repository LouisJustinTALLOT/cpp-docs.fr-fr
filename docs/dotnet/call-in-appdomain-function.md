---
title: call_in_appdomain, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: da0f2bc1a503226e41198871e6dc48ace7a86854
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988537"
---
# <a name="call_in_appdomain-function"></a>call_in_appdomain, fonction

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

#### <a name="parameters"></a>Parameters

*appdomainId*<br/>
AppDomain dans lequel appeler la fonction.

*voidFunc*<br/>
Pointeur vers une fonction `void` qui accepte N paramètres (0 < = N < = 15).

*nonvoidFunc*<br/>
Pointeur vers une fonction non`void` qui accepte N paramètres (0 < = N < = 15).

*arg1...argN*<br/>
Zéro à 15 paramètres à passer à `voidFunc` ou `nonvoidFunc` dans l’autre AppDomain.

## <a name="return-value"></a>Valeur de retour

Résultat de l’exécution de `voidFunc` ou `nonvoidFunc` dans le domaine d’application spécifié.

## <a name="remarks"></a>Notes

Les arguments de la fonction passée à `call_in_appdomain` ne doivent pas être des types CLR.

## <a name="example"></a>Exemple

```cpp
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

## <a name="output"></a>Output

```
default appdomain: msl_call_in_appdomain.exe
in appDomain1: First Domain
default appdomain id = 1
appDomain1 id = 2
```

## <a name="requirements"></a>Configuration requise pour

**Fichier d’en-tête** \<msclr\appdomain.h >

**Espace de noms** msclr,
