---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 11/04/2016
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
ms.openlocfilehash: 22cf8eeb5f99b6abee624aa3b1d06246d7230652
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156822"
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Convertit des caractères JIS (Japan Industry Standard) en caractères JMS(Microsoft Japan) ou des caractères JMS en caractères JIS.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Caractère à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Dans les paramètres régionaux japonais, ces fonctions retournent un caractère converti ou retournent 0 si aucune conversion n’est possible. Dans les paramètres régionaux non japonais, ces fonctions retournent le caractère passé.

## <a name="remarks"></a>Notes

Le **_mbcjistojms** fonction convertit un caractère Standard JIS (Japan Industry) en un caractère Microsoft Kanji (Shift JIS). Le caractère est converti que si les octets de tête et de fin se trouvent dans la plage 0 x 21 - 0x7E. Si le responsable ou un octet d’évaluation est en dehors de cette plage, **errno** a la valeur **EILSEQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Le **_mbcjmstojis** fonction convertit un caractère Shift JIS en caractère JIS. Le caractère est converti que si l’octet de tête est dans la plage 0 x 81-0x9F ou 0xE0 - 0xFC et l’octet de fin est dans la plage 0 x 40-0x7E ou 0 x 80 - 0xFC. Notez que cette plage comporte certains codes de caractère auxquels aucun caractère n’est assigné et qui, de ce fait, ne peuvent pas être convertis.

La valeur *c* doit être une valeur 16 bits dont 8 bits de gauche représentent l’octet de tête du caractère à convertir et dont 8 bits de poids faible représentent l’octet de fin.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions antérieures, **_mbcjistojms** et **_mbcjmstojis** ont été appelées **jistojms** et **jmstojis**, respectivement. **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** et **_mbcjmstojis_l** doit être utilisé à la place.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
