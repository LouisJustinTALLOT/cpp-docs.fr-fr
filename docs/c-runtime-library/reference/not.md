---
description: 'En savoir plus sur :'
title: not
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- std::not
- std.not
- Not
helpviewer_keywords:
- not function
ms.assetid: d2ddbd5c-33c0-4aff-8961-feac155b4ba1
ms.openlocfilehash: ea70ce27ad496f2231490ebbbcf75ec905990c60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256287"
---
# <a name="not"></a>not

Alternative à l’opérateur ! .

## <a name="syntax"></a>Syntaxe

```C

#define not !
```

## <a name="remarks"></a>Notes

La macro génère l'opérateur !.

## <a name="example"></a>Exemple

```cpp
// iso646_not.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 0;

   if (!a)
      cout << "a is zero" << endl;

   if (not(a))
      cout << "a is zero" << endl;
}
```

```Output
a is zero
a is zero
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<iso646.h>
