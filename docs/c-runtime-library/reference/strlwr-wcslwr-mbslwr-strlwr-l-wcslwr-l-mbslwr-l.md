---
description: 'En savoir plus sur : _strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l'
title: _strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l
ms.date: 4/2/2020
api_name:
- _strlwr_l
- _strlwr
- _wcslwr_l
- _mbslwr_l
- _wcslwr
- _mbslwr
- _o__mbslwr
- _o__mbslwr_l
- _o__strlwr
- _o__strlwr_l
- _o__wcslwr
- _o__wcslwr_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strlwr
- wcslwr_l
- _ftcslwr
- mbslwr_l
- _mbslwr
- _wcslwr
- strlwr_l
- _tcslwr
- mbslwr
helpviewer_keywords:
- tcslwr function
- _strlwr function
- converting case
- string conversion [C++], case
- mbslwr function
- _strlwr_l function
- strlwr_l function
- _wcslwr function
- ftcslwr function
- strings [C++], case
- _tcslwr_l function
- _wcslwr_l function
- wcslwr_l function
- mbslwr_l function
- tcslwr_l function
- _tcslwr function
- converting case, CRT functions
- _ftcslwr function
- _mbslwr function
- case, converting
- strings [C++], converting case
- _mbslwr_l function
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
ms.openlocfilehash: 7d0d103185494d26890fc62061ebd16c168fc477
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344807"
---
# <a name="_strlwr-_wcslwr-_mbslwr-_strlwr_l-_wcslwr_l-_mbslwr_l"></a>_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l

Convertit une chaîne en minuscules. Il existe des versions plus sécurisées de ces fonctions. Consultez [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).

> [!IMPORTANT]
> **_mbslwr** et **_mbslwr_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strlwr(
   char * str
);
wchar_t *_wcslwr(
   wchar_t * str
);
unsigned char *_mbslwr(
   unsigned char * str
);
char *_strlwr_l(
   char * str,
   _locale_t locale
);
wchar_t *_wcslwr_l(
   wchar_t * str,
   _locale_t locale
);
unsigned char *_mbslwr_l(
   unsigned char * str,
   _locale_t locale
);
template <size_t size>
char *_strlwr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcslwr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbslwr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strlwr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcslwr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbslwr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne se terminant par un caractère Null à convertir en minuscules.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne un pointeur désignant la chaîne convertie. Sachant que la modification est effectuée sur place, le pointeur retourné est le même que celui passé comme argument d’entrée. Aucune valeur de retour n'est réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

La fonction **_strlwr** convertit toutes les lettres majuscules de *Str* en minuscules, comme déterminé par le paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Les autres caractères ne sont pas concernés. Pour plus d’informations sur les **LC_CTYPE**, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_L** utilisent les paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Les fonctions **_wcslwr** et **_mbslwr** sont des versions à caractères larges et à caractères multioctets de **_strlwr**. L’argument et la valeur de retour de **_wcslwr** sont des chaînes à caractères larges ; ceux de **_mbslwr** sont des chaînes de caractères multioctets. Ces trois fonctions se comportent sinon de façon identique.

Si *Str* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent la chaîne d’origine et attribuent à **errno** la valeur **EINVAL**.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr**|**_strlwr**|**_mbslwr**|**_wcslwr**|
|**_tcslwr_l**|**_strlwr_l**|**_mbslwr_l**|**_wcslwr_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strlwr**, **_strlwr_l**|\<string.h>|
|**_wcslwr**, **_wcslwr_l**|\<string.h> ou \<wchar.h>|
|**_mbslwr**, **_mbslwr_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strlwr.c
// compile with: /W3
// This program uses _strlwr and _strupr to create
// uppercase and lowercase copies of a mixed-case string.
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The String to End All Strings!";
   char * copy1 = _strdup( string ); // make two copies
   char * copy2 = _strdup( string );

   _strlwr( copy1 ); // C4996
   // Note: _strlwr is deprecated; consider using _strlwr_s instead
   _strupr( copy2 ); // C4996
   // Note: _strupr is deprecated; consider using _strupr_s instead

   printf( "Mixed: %s\n", string );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)<br/>
