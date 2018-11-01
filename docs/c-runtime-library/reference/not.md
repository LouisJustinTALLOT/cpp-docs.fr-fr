---
title: not
ms.date: 11/04/2016
apilocation:
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
apitype: DLLExport
f1_keywords:
- std::not
- std.not
- Not
helpviewer_keywords:
- not function
ms.assetid: d2ddbd5c-33c0-4aff-8961-feac155b4ba1
ms.openlocfilehash: bc20ab25470b10d21c19ded695343f196090f801
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514762"
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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iso646.h>