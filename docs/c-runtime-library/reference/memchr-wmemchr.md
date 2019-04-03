---
title: memchr, wmemchr
ms.date: 03/31/2019
apiname:
- wmemchr
- memchr
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: 00a1f0d12047cc388b56074a657ffd739e986827
ms.sourcegitcommit: 489c0b998f2360317701f7a4a97b2b8ad96052d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866914"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Rechercher des caractères dans une mémoire tampon.

## <a name="syntax"></a>Syntaxe

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Pointeur désignant la mémoire tampon.

*c*<br/>
Caractère à rechercher.

*count*<br/>
Nombre de caractères à vérifier.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne un pointeur vers le premier emplacement de *c* dans *tampon*. Sinon, elle retourne NULL.

## <a name="remarks"></a>Notes

`memchr` et `wmemchr` rechercher la première occurrence de *c* dans la première *nombre* caractères de *tampon*. Il s’arrête lorsqu’il trouve *c* ou qu’elles ont vérifié la première *nombre* caractères.

En C, ces fonctions prennent une **const** pointeur pour le premier argument. En C++, deux surcharges sont disponibles. La surcharge acceptant un pointeur vers **const** retourne un pointeur vers **const**; la version qui accepte un pointeur vers non -**const** retourne un pointeur vers non -**const** . La macro \_CRT\_CONST\_CORRECT\_surcharges est défini si les deux le **const** et non-**const** versions de ces fonctions sont disponibles. Si vous avez besoin non -**const** comportement pour les deux surcharges C++ dans C++, définissez le symbole \_CONST\_retourner.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`memchr`|\<memory.h> ou \<string.h>|
|`wmemchr`|\<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>Sortie

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
