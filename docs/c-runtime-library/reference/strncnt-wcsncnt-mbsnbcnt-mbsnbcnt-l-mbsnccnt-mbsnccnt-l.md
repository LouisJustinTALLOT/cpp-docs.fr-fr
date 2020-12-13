---
description: 'En savoir plus sur : _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l'
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 9030c66e226cc36e08ca1730a8178b0000216d9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344742"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Retourne le nombre de caractères ou d’octets indiqué dans un paramètre count.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt** et **_mbsnccnt_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Nombre de caractères ou d’octets à examiner dans *Str*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_mbsnbcnt** et **_mbsnbcnt_l** retournent le nombre d’octets trouvés dans le premier *nombre* de caractères multioctets de *Str*. **_mbsnccnt** et **_mbsnccnt_l** retournent le nombre de caractères trouvés dans le premier *nombre* d’octets de *Str*. Si un caractère NULL est rencontré avant la fin de l’examen de *Str* , il retourne le nombre d’octets ou de caractères trouvés avant le caractère null. Si *Str* est inférieur à *Count* caractères ou bytes, ils retournent le nombre de caractères ou d’octets dans la chaîne. Si *Count* est inférieur à zéro, elles retournent 0. Dans les versions précédentes, ces fonctions avaient une valeur de retour de type **`int`** au lieu de **size_t**.

**_strncnt** retourne le nombre de caractères dans le premier *nombre* d’octets de la chaîne codée sur un *octet.* **_wcsncnt** retourne le nombre de caractères dans le premier *nombre* de caractères larges de la chaîne de caractères larges *Str*.

## <a name="remarks"></a>Notes

**_mbsnbcnt** et **_mbsnbcnt_l** comptent le nombre d’octets trouvés dans le premier *nombre* de caractères multioctets de *Str*. **_mbsnbcnt** et **_mbsnbcnt_l** remplacer **mtob** et doivent être utilisés à la place de **mtob**.

**_mbsnccnt** et **_mbsnccnt_l** comptent le nombre de caractères trouvés dans le premier *nombre* d’octets de *Str*. Si **_mbsnccnt** et **_mbsnccnt_l** rencontrent un caractère NULL dans le deuxième octet d’un caractère codé sur deux octets, le premier octet est également considéré comme null et n’est pas inclus dans la valeur de nombre retournée. **_mbsnccnt** et **_mbsnccnt_l** remplacer **btom** et doivent être utilisés à la place de **btom**.

Si *Str* est un pointeur **null** ou si le *nombre* est égal à 0, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md), **errno** a la valeur **EINVAL** et la fonction retourne 0.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|n/a|
|**_wcsncnt**|n/a|n/a|**_mbsnbcnt**|
|**_wcsncnt**|n/a|n/a|**_mbsnccnt**|
|n/a|n/a|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
