---
title: _memccpy
ms.date: 11/04/2016
apiname:
- _memccpy
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _memccpy
helpviewer_keywords:
- _memccpy function
- memccpy function
ms.assetid: 9a2337df-6e85-4eba-b247-dd0532f45ddb
ms.openlocfilehash: 704aab84ea3e39c91def1d4ac8b6d2d9d3650759
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499688"
---
# <a name="_memccpy"></a>_memccpy

Copie des caractères à partir de la mémoire tampon.

## <a name="syntax"></a>Syntaxe

```C
void *_memccpy(
   void *dest,
   const void *src,
   int c,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Pointeur désignant la destination.

*src*<br/>
Pointeur désignant la source.

*c*<br/>
Dernier caractère à copier.

*count*<br/>
Nombre de caractères.

## <a name="return-value"></a>Valeur de retour

Si le caractère *c* est copié, **_memccpy** retourne un pointeur vers le caractère dans *dest* qui suit immédiatement le caractère. Si *c* n’est pas copié, la **valeur null**est retournée.

## <a name="remarks"></a>Notes

La fonction **_memccpy** copie 0 ou plusieurs caractères de *src* vers *dest*, en s’arrêtant lorsque le caractère *c* a été copié ou lorsque les *nombres* de caractères ont été copiés, selon ce qui se produit en premier.

**Remarque relative à la sécurité** Vérifiez que la mémoire tampon de destination est d’une taille identique ou supérieure à celle de la mémoire tampon source. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_memccpy**|\<memory.h> ou \<string.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_memccpy.c

#include <memory.h>
#include <stdio.h>
#include <string.h>

char string1[60] = "The quick brown dog jumps over the lazy fox";

int main( void )
{
   char buffer[61];
   char *pdest;

   printf( "Function: _memccpy 60 characters or to character 's'\n" );
   printf( "Source: %s\n", string1 );
   pdest = _memccpy( buffer, string1, 's', 60 );
   *pdest = '\0';
   printf( "Result: %s\n", buffer );
   printf( "Length: %d characters\n", strlen( buffer ) );
}
```

### <a name="output"></a>Sortie

```Output
Function: _memccpy 60 characters or to character 's'
Source: The quick brown dog jumps over the lazy fox
Result: The quick brown dog jumps
Length: 25 characters
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
