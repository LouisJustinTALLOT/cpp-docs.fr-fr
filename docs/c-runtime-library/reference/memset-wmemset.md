---
title: memset, wmemset
description: 'En savoir plus sur : memset, wmemset'
ms.date: 1/15/2021
api_name:
- wmemset
- memset
- _o_memset
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memset
- wmemset
helpviewer_keywords:
- wmemset function
- memset function
ms.openlocfilehash: 1ee5b3cb3653a3d5486eecb0f3b033e69d9db9fa
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563963"
---
# <a name="memset-wmemset"></a>`memset`, `wmemset`

Définit des mémoires tampons sur un caractère spécifié.

## <a name="syntax"></a>Syntaxe

```C
void *memset(
   void *dest,
   int c,
   size_t count
);
wchar_t *wmemset(
   wchar_t *dest,
   wchar_t c,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*`dest`*\
Pointeur désignant la destination.

*`c`*\
Caractère à définir.

*`count`*\
Nombre de caractères.

## <a name="return-value"></a>Valeur renvoyée

Valeur de *`dest`* .

## <a name="remarks"></a>Remarques

Définit les premiers *`count`* caractères de *`dest`* sur le caractère *`c`* .

**Note de sécurité** Assurez-vous que la mémoire tampon de destination a suffisamment d’espace pour au moins *`count`* caractères. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`memset`**|`<memory.h>` ou `<string.h>`|
|**`wmemset`**|`<wchar.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_memset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <memory.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is a test of the memset function";

   printf( "Before: %s\n", buffer );
   memset( buffer, '*', 4 );
   printf( "After:  %s\n", buffer );
}
```

### <a name="output"></a>Sortie

```Output
Before: This is a test of the memset function
After:  **** is a test of the memset function
```

Voici un exemple d’utilisation de wmemset :

```C
// crt_wmemset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <wchar.h>
#include <stdio.h>

int main( void )
{
   wchar_t buffer[] = L"This is a test of the wmemset function";

   wprintf( L"Before: %s\n", buffer );
   wmemset( buffer, '*', 4 );
   wprintf( L"After:  %s\n", buffer );
}
```

### <a name="output"></a>Sortie

```Output
Before: This is a test of the wmemset function
After:  **** is a test of the wmemset function
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memchr`, `wmemchr`](memchr-wmemchr.md)\
[`memcmp`, `wmemcmp`](memcmp-wmemcmp.md)\
[`memcpy`, wmemcpy](memcpy-wmemcpy.md)\
[`_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l`](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)