---
description: 'En savoir plus sur : macro _countof'
title: _countof Macro
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 190f47aa7bb6bcf6bbd9478cce9df90aca81b437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146456"
---
# <a name="_countof-macro"></a>_countof Macro

Calcule le nombre d’éléments dans un tableau alloué statiquement.

## <a name="syntax"></a>Syntaxe

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Paramètres

*array*<br/>
Nom d'un tableau.

## <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans le tableau, exprimé sous la forme d’un **size_t**.

## <a name="remarks"></a>Notes

**_countof** est implémentée en tant que macro de préprocesseur de type fonction. La version C++ dispose d’une machine de modèle supplémentaire à détecter au moment de la compilation si un pointeur est passé au lieu d’un tableau déclaré statiquement.

Assurez-vous que le *tableau* est en fait un tableau, et non un pointeur. En C, **_countof** produit des résultats erronés si *Array* est un pointeur. En C++, **_countof** ne parvient pas à compiler si le *tableau* est un pointeur.  Un tableau passé en tant que paramètre à une fonction s' *atténue à un pointeur*, ce qui signifie que dans la fonction, vous ne pouvez pas utiliser **_countof** pour déterminer l’étendue du tableau.

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

[sizeof (opérateur)](../../cpp/sizeof-operator.md)<br/>
