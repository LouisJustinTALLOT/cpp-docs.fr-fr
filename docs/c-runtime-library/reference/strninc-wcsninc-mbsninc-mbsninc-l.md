---
title: _strninc, _wcsninc, _mbsninc, _mbsninc_l
ms.date: 4/2/2020
api_name:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
- _o__mbsninc
- _o__mbsninc_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
ms.openlocfilehash: 297d2fdf940ab81a3d636d4726e6e6a345ce5c02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364481"
---
# <a name="_strninc-_wcsninc-_mbsninc-_mbsninc_l"></a>_strninc, _wcsninc, _mbsninc, _mbsninc_l

Avance un pointeur de cordes par **n** caractères.

> [!IMPORTANT]
> **_mbsninc** et **_mbsninc_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strninc(
   const char *str,
   size_t count
);
wchar_t *_wcsninc(
   const wchar_t *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Chaîne source.

*count*<br/>
Nombre de caractères dont un pointeur de chaîne est incrémenté.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne un pointeur à *str* après *str* a été incrémenté par des personnages *de comptage* ou **NULL** si le pointeur fourni est **NULL**. Si *le nombre* est supérieur ou égal au nombre de caractères en *str,* le résultat n’est pas défini.

## <a name="remarks"></a>Notes

Le **_mbsninc** fonction incréments *str* par *compte* des caractères multioctets. **_mbsninc** reconnaît les séquences multioctets selon la [page de code multioctet](../../c-runtime-library/code-pages.md) actuellement en service.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsninc**|**_strninc**|**_mbsninc**|**_wcsninc**|

**_strninc** et **_wcsninc** sont des versions de cordes à caractère unique et à caractère large de **_mbsninc**. **_wcsninc** et **_strninc** ne sont fournis que pour cette cartographie et ne doivent pas être utilisés autrement. Pour plus d’informations, consultez [Utilisation de mappages de texte générique](../../c-runtime-library/using-generic-text-mappings.md) et [Mappages de texte générique](../../c-runtime-library/generic-text-mappings.md).

**_mbsninc_l** est identique, sauf qu’il utilise le paramètre local passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsninc**|\<mbstring.h>|
|**_mbsninc_l**|\<mbstring.h>|
|**_strninc**|\<tchar.h>|
|**_wcsninc**|\<tchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
