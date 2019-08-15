---
title: _strinc, _wcsinc, _mbsinc, _mbsinc_l
ms.date: 11/04/2016
apiname:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
ms.openlocfilehash: 48bc7caa5dbc2d2e7eec847bfa5135d13bcd83c0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499468"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l

Avance un pointeur de chaîne d'un caractère.

> [!IMPORTANT]
> **_mbsinc** et **_mbsinc_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strinc(
   const char *current,
   _locale_t locale
);
wchar_t *_wcsinc(
   const wchar_t *current,
   _locale_t locale
);
unsigned char *_mbsinc(
   const unsigned char *current
);
unsigned char *_mbsinc_l(
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*current*<br/>
Pointeur de caractère.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne un pointeur vers le caractère qui suit immédiatement le *actuel*.

## <a name="remarks"></a>Notes

La fonction **_mbsinc** retourne un pointeur vers le premier octet du caractère multioctet qui suit immédiatement le *actuel*. **_mbsinc** reconnaît les séquences de caractères multioctets en fonction de la [page de codes multioctets](../../c-runtime-library/code-pages.md) en cours d’utilisation; **_mbsinc_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

La fonction de texte générique **_tcsinc**, définie dans Tchar. h, est mappée à **_Mbsinc** si **_ MBCS** a été défini, ou à **_wcsinc** si **_ Unicode** a été défini. Sinon, **_tcsinc** est mappé à **_strinc**. **_strinc** et **_wcsinc** sont des versions à caractères codés sur un octet et à caractères larges de **_mbsinc**. **_strinc** et **_wcsinc** sont fournis uniquement pour ce mappage et ne doivent pas être utilisés dans le cas contraire. Pour plus d’informations, consultez [Utilisation de mappages de texte générique](../../c-runtime-library/using-generic-text-mappings.md) et [Mappages de texte générique](../../c-runtime-library/generic-text-mappings.md).

Si *Current* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **EINVAL** et définit **errno** sur **EINVAL**.

> [!IMPORTANT]
> Ces fonctions peuvent être vulnérables aux menaces de dépassement de mémoire tampon. Les dépassements de mémoire tampon peuvent être utilisés pour les attaques du système, car ils peuvent provoquer une élévation des privilèges injustifiée. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h>|
|**_wcsinc**|\<tchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
