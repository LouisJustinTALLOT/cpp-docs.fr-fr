---
title: memmove, wmemmove
ms.date: 11/04/2016
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 988af1c2678e20ea40ce4dfe331a3b6c49db0547
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156562"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Déplace une mémoire tampon vers une autre. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md).

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

*dest*<br/>
Objet de destination.

*src*<br/>
Objet source.

*count*<br/>
Nombre d’octets (**memmove**) ou de caractères (**wmemmove**) à copier.

## <a name="return-value"></a>Valeur de retour

La valeur de *dest*.

## <a name="remarks"></a>Notes

Copies *nombre* octets (**memmove**) ou de caractères (**wmemmove**) à partir de *src* à *dest*. Si certaines régions de la zone source et de la destination se chevauchent, les deux fonctions garantissent que les octets source d’origine dans la région de chevauchement sont copiés avant d’être remplacés.

**Remarque relative à la sécurité** Vérifiez que la mémoire tampon de destination est d’une taille identique ou supérieure à celle de la mémoire tampon source. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

Le **memmove** et **wmemmove** fonctions seront déconseillées seulement si la constante **_CRT_SECURE_DEPRECATE_MEMORY** est défini avant l’instruction d’inclusion dans l’ordre pour les fonctions déconseillées, comme illustré dans l’exemple ci-dessous :

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
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
