---
title: _mbbtombc, _mbbtombc_l
ms.date: 11/04/2016
api_name:
- _mbbtombc_l
- _mbbtombc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 244e603a3234b755d19a1c1d0738e8c22d74b8e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952733"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc, _mbbtombc_l

Convertit un caractère multioctet codé sur un octet en caractère multioctet codé sur deux octets correspondant.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère codé sur un octet à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Si **_mbbtombc** convertit correctement *c*, il retourne un caractère multioctet ; Sinon, elle retourne *c*.

## <a name="remarks"></a>Notes

La fonction **_mbbtombc** convertit un caractère multioctet codé sur un octet donné en caractère multioctet codé sur deux octets correspondant. Les caractères doivent être compris dans la plage 0x20-0x7E ou 0xA1-0xDF à convertir.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . Les versions de cette fonction sont identiques, sauf que **_mbbtombc** utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux et **_mbbtombc_l** à la place utilise les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions antérieures, **_mbbtombc** était nommé **hantozen**. Pour le nouveau code, utilisez **_mbbtombc**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
