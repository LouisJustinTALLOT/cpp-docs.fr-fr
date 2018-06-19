---
title: _countof Macro | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _countof
- countof
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30df64b045e2af6181d343a4eafb962d22eaa05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394741"
---
# <a name="countof-macro"></a>_countof Macro

Calcule le nombre d’éléments dans un tableau alloué de manière statique.

## <a name="syntax"></a>Syntaxe

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Paramètres

*array*<br/>
Nom d'un tableau.

## <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le tableau, exprimé comme une **size_t**.

## <a name="remarks"></a>Notes

**_countof** est implémenté comme une macro de préprocesseur type fonction. La version C++ a machines modèle supplémentaire pour détecter au moment de la compilation si un pointeur est passé au lieu d’un tableau déclaré statiquement.

Vérifiez que *tableau* est en réalité un tableau, et non un pointeur. En C, **_countof** génère des résultats erronés si *tableau* est un pointeur. En C++, **_countof** ne parvient pas à compiler si *tableau* est un pointeur.  Un tableau passé en tant que paramètre à une fonction *décline à un pointeur*, ce qui signifie que la fonction, vous ne pouvez pas utiliser **_countof** pour déterminer l’étendue du tableau.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>Exemple

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>Voir aussi

[sizeof, opérateur](../../cpp/sizeof-operator.md)<br/>
