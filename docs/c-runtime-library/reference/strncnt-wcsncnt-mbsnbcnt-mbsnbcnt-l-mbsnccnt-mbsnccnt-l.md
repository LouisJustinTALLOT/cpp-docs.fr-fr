---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 11/04/2016
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 456a11ae98fe8fb40c2ef1d6f4e6d86583f4b7b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209819"
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Retourne le nombre de caractères ou d’octets indiqué dans un paramètre count.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**, et **_mbsnccnt_l** ne peut pas être utilisé dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne à examiner.

*count*<br/>
Nombre de caractères ou d’octets à examiner dans *str*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_mbsnbcnt** et **_mbsnbcnt_l** retourner le nombre d’octets trouvés dans la première *nombre* caractères multioctets de *str*. **_mbsnccnt** et **_mbsnccnt_l** retourner le nombre de caractères trouvés dans la première *nombre* d’octets de *str*. Si un caractère null est rencontré avant l’examen de *str* a terminé, elles retournent le nombre d’octets ou caractères trouvés avant le caractère null. Si *str* comporte moins de *nombre* caractères ou octets, elles retournent le nombre de caractères ou d’octets dans la chaîne. Si *nombre* est inférieur à zéro, elles retournent 0. Dans les versions précédentes, ces fonctions retournaient une valeur de type **int** plutôt que **size_t**.

**_strncnt** retourne le nombre de caractères dans la première *nombre* octets de la chaîne d’un octet *str*. **_wcsncnt** retourne le nombre de caractères dans la première *nombre* caractères larges de la chaîne de caractères larges *str*.

## <a name="remarks"></a>Notes

**_mbsnbcnt** et **_mbsnbcnt_l** compter le nombre d’octets trouvés dans la première *nombre* caractères multioctets de *str*. **_mbsnbcnt** et **_mbsnbcnt_l** remplacer **mtob** et doit être utilisé à la place de **mtob**.

**_mbsnccnt** et **_mbsnccnt_l** compter le nombre de caractères trouvés dans la première *nombre* d’octets de *str*. Si **_mbsnccnt** et **_mbsnccnt_l** rencontrer un caractère null dans le deuxième octet d’un caractère sur deux octets, le premier octet est également considéré comme null et n’est pas inclus dans la valeur de count retournée. **_mbsnccnt** et **_mbsnccnt_l** remplacer **btom** et doit être utilisé à la place de **btom**.

Si *str* est un **NULL** pointeur ou est *nombre* est 0, ces fonctions appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md), **errno** a la valeur **EINVAL**, et la fonction retourne 0.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|N/A|
|**_wcsncnt**|N/A|N/A|**_mbsnbcnt**|
|**_wcsncnt**|N/A|N/A|**_mbsnccnt**|
|N/A|N/A|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Sortie

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
