---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Décrit les fonctions Microsoft C Runtime Library (CRT) _mbclen, mblen, _mblen_l et _mbclen_l.
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341121"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Obtient la longueur et détermine la validité d’un caractère multioctet.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*C*\
Caractères multioctet.

*mbstr*\
Adresse d’une séquence d’octets de caractères multioctets.

*Compter*\
Nombre d'octets à vérifier.

*locale*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_mbclen** et **_mbclen_l** retourner 1 ou 2, selon la longueur du caractère multioctet *c*. Les fonctions retournent toujours 1 pour UTF-8, que *ce* soit c est multioctet ou non. Il n’y a pas de retour d’erreur pour **_mbclen**.

Si *mbstr* n’est pas **NULL,** **mblen** et **_mblen_l** retourner la longueur, dans les octets, du caractère multioctet. Les fonctions **mblen** et **_mblen_l** fonctionnent correctement sur UTF-8, et peuvent retourner une valeur comprise entre 1 et 3. Lorsque *mbstr* est **NULL** (ou il pointe vers le caractère nul de caractère large), **mblen** et **_mblen_l** retour 0. L’objet qui *pointe mbstr* doit former un caractère multioctet valide dans les caractères du premier *compte,* ou **mblen** et **_mblen_l** retour -1.

## <a name="remarks"></a>Notes

La fonction **_mbclen** renvoie la longueur, dans les octets, du caractère multioctet *c*. Si *c* ne pointe pas vers le point de plomb byte d’un caractère multioctet (tel que déterminé par un appel implicite à [_ismbblead](ismbblead-ismbblead-l.md), le résultat de **_mbclen** est imprévisible.

**mblen** retourne la longueur dans les octets de *mbstr* si c’est un caractère multioctet valide. Il détermine également la validité multioctet-caractère associée à la page de code. **mblen** examine *le nombre* ou moins d’octets contenus dans *mbstr,* mais pas plus de **MB_CUR_MAX** octets.

La valeur de sortie est affectée par le **LC_CTYPE’établissement** de la catégorie de l’endroit. Les versions de ces fonctions sans le **suffixe _l** utilisent le lieu actuel pour ce comportement local-dépendant. Les **versions _l** suffixes se comportent de la même façon, mais elles utilisent le paramètre local passé à la place. Pour plus d’informations, voir [setlocale](setlocale-wsetlocale.md) et [Local](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**, et **_mbclen_l** sont spécifiques à Microsoft, ne font pas partie de la bibliothèque Standard C. Nous ne vous recommandons pas de les utiliser là où vous voulez du code portable. Pour la compatibilité standard C, utilisez **mblen** ou **mbrlen** à la place.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Mappe à la macro ou à la fonction inline|**_mbclen**|Mappe à la macro ou à la fonction inline|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>Voir aussi

[Classification des caractères](../../c-runtime-library/character-classification.md)\
[Local](../../c-runtime-library/locale.md)\
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen (mbrlen)](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
