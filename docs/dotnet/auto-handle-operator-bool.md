---
title: auto_handle::operator (bool)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_handle.operator bool
- msclr.auto_handle.operator bool
- operator bool
- msclr::auto_handle::operator bool
- auto_handle::operator bool
helpviewer_keywords:
- auto_handle::operator bool
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
ms.openlocfilehash: 95a4b324194b2e1adf8cc9596f8e2440379e5a47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565943"
---
# <a name="autohandleoperator-bool"></a>auto_handle::operator (bool)

Opérateur pour l’utilisation de `auto_handle` dans une expression conditionnelle.

## <a name="syntax"></a>Syntaxe

```
operator bool();
```

## <a name="return-value"></a>Valeur de retour

**true** si l’objet encapsulé est valide ; **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Cet opérateur convertit effectivement `_detail_class::_safe_bool` qui est plus sûr que **bool** , car il ne peut pas être converti en un type intégral.

## <a name="example"></a>Exemple

```
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
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

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[auto_handle, membres](../dotnet/auto-handle-members.md)<br/>
[auto_handle::operator!](../dotnet/auto-handle-operator-logical-not.md)