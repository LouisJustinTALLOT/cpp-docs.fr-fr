---
title: auto_gcroot::operator bool | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_gcroot.operator bool
- auto_gcroot::operator bool
- msclr.auto_gcroot.operator bool
- msclr::auto_gcroot::operator bool
- operator bool
dev_langs:
- C++
helpviewer_keywords:
- bool operator
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2fe517809db7cecacc7a0190e0dae94ef55c35d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161188"
---
# <a name="autogcrootoperator-bool"></a>auto_gcroot::operator bool

Opérateur pour l’utilisation de `auto_gcroot` dans une expression conditionnelle.

## <a name="syntax"></a>Syntaxe

```
operator bool() const;
```

## <a name="return-value"></a>Valeur de retour

**true** si l’objet encapsulé est valide ; **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Cet opérateur convertit effectivement `_detail_class::_safe_bool` qui est plus sûr que **bool** , car il ne peut pas être converti en un type intégral.

## <a name="example"></a>Exemple

```cpp
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

[auto_gcroot Members](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::operator!](../dotnet/auto-gcroot-operator-logical-not.md)