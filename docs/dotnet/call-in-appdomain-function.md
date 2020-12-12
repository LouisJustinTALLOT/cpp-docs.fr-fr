---
description: 'En savoir plus sur : fonction call_in_appdomain'
title: call_in_appdomain, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: ece4929e2b99b09f3c9148b50c609ec1b5596b3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282573"
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

#### <a name="parameters"></a>Paramètres

*appdomainId*<br/>
AppDomain dans lequel appeler la fonction.

*voidFunc*<br/>
Pointeur vers une **`void`** fonction qui accepte N paramètres (0 <= N <= 15).

*nonvoidFunc*<br/>
Pointeur vers une **`void`** fonction qui accepte n paramètres (0 <= n <= 15).

*arg1... argN*<br/>
Zéro à 15 paramètres à passer à `voidFunc` ou à `nonvoidFunc` l’autre AppDomain.

## <a name="return-value"></a>Valeur renvoyée

Résultat de l’exécution de `voidFunc` ou `nonvoidFunc` dans le domaine d’application spécifié.

## <a name="remarks"></a>Notes

Les arguments de la fonction passée à ne `call_in_appdomain` doivent pas être des types CLR.

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

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr\appdomain.h>

**Espace de noms** msclr,
