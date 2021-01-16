---
description: 'En savoir plus sur : memmove, wmemmove'
title: memmove, wmemmove
ms.date: 1/14/2021
api_name:
- memmove
- wmemmove
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.openlocfilehash: 6f9942c232710585aa5837510f0f04e5db36fb2a
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243123"
---
# <a name="memmove-wmemmove"></a>`memmove`, `wmemmove`

Déplace une mémoire tampon vers une autre Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [ `memmove_s` , `wmemmove_s` ](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*`dest`*\
Objet de destination.

*`src`*\
Objet source.

*`count`*\
Nombre d’octets ( **`memmove`** ) ou de caractères ( **`wmemmove`** ) à copier.

## <a name="return-value"></a>Valeur renvoyée

Valeur de *`dest`* .

## <a name="remarks"></a>Remarques

Copie les *`count`* octets ( **`memmove`** ) ou les caractères ( **`wmemmove`** ) de *`src`* vers *`dest`* . Si certaines régions de la zone source et de la destination se chevauchent, les deux fonctions garantissent que les octets source d’origine dans la région de chevauchement sont copiés avant d’être remplacés.

**Remarque relative à la sécurité** Vérifiez que la mémoire tampon de destination est d’une taille identique ou supérieure à celle de la mémoire tampon source. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

Les **`memmove`** **`wmemmove`** fonctions et seront dépréciées uniquement si la constante **`_CRT_SECURE_DEPRECATE_MEMORY`** est définie avant l’instruction d’inclusion pour que les fonctions soient dépréciées, comme dans l’exemple ci-dessous :

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

ou

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`memmove`**|`<string.h>`|
|**`wmemmove`**|`<wchar.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memcpy`, `wmemcpy`](memcpy-wmemcpy.md)\
[`strcpy`, `wcscpy`, `_mbscpy`](strcpy-wcscpy-mbscpy.md)\
[`strncpy`, `_strncpy_l`, `wcsncpy`, `_wcsncpy_l`, `_mbsncpy`, `_mbsncpy_l`](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)\
