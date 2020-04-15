---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 4/2/2020
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
- _o__mbcjistojms
- _o__mbcjistojms_l
- _o__mbcjmstojis
- _o__mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: ef0010088543f1c580e536f120cae681a7582491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341182"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Convertit des caractères JIS (Japan Industry Standard) en caractères JMS(Microsoft Japan) ou des caractères JMS en caractères JIS.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Caractère à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Dans les paramètres régionaux japonais, ces fonctions retournent un caractère converti ou retournent 0 si aucune conversion n’est possible. Dans les paramètres régionaux non japonais, ces fonctions retournent le caractère passé.

## <a name="remarks"></a>Notes

La fonction **_mbcjistojms** convertit un personnage de Japan Industry Standard (JIS) en un personnage microsoft Kanji (Shift JIS). Le personnage n’est converti que si les octets de plomb et de piste sont dans la gamme 0x21 - 0x7E. Si le byte de plomb ou d’essai est en dehors de cette plage, **errno** est réglé à **EILSEQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La fonction **_mbcjmstojis** convertit un personnage Shift JIS en un personnage JIS. Le personnage n’est converti que si le byte de plomb est dans la gamme 0x81 - 0x9F ou 0xE0 - 0xFC et le byte de traînée est dans la gamme 0x40 - 0x7E ou 0x80 - 0xFC. Notez que cette plage comporte certains codes de caractère auxquels aucun caractère n’est assigné et qui, de ce fait, ne peuvent pas être convertis.

La valeur *c* devrait être une valeur 16 bits dont les 8 bits supérieurs représentent le byte de plomb du personnage à convertir et dont les 8 bits inférieurs représentent le byte de piste.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions précédentes, **_mbcjistojms** et **_mbcjmstojis** ont été appelés **jistojms** et **jmstojis**, respectivement. **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** et **_mbcjmstojis_l** devraient être utilisés à la place.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[routines _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
