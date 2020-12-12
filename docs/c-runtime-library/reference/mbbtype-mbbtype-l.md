---
description: 'En savoir plus sur : _mbbtype, _mbbtype_l'
title: _mbbtype, _mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: 6a646682144acb346827eaa78382915f026fa455
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299603"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Retourne le type d'octet en se basant sur l'octet précédent.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à tester.

*type*<br/>
Type d'octet à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_mbbtype** retourne le type d’octet dans une chaîne. Cette décision est contextuelle, comme spécifié par la valeur de *type*, qui fournit la condition de test de contrôle. *type* est le type de l’octet précédent dans la chaîne. Les constantes manifestes présentes dans le tableau suivant sont définies dans Mbctype.h.

|Valeur de *type*|tests de **_mbbtype** pour|Valeur retournée|*c*|
|---------------------|--------------------------|------------------|---------|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_SINGLE** (0)|Octet unique (0x20-0x7E, 0xA1-0xDF)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_LEAD** (1)|Octet de tête d’un caractère multioctet (0x81-0x9F, 0xE0-0xFC)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_ILLEGAL**<br /><br /> (-1)|Caractère non valide (n’importe quelle valeur, à l’exception de 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|
|1|Octet de fin valide|**_MBC_TRAIL** (2)|Octet de fin d’un caractère multioctet (0x40-0x7E, 0x80-0xFC)|
|1|Octet de fin valide|**_MBC_ILLEGAL**<br /><br /> (-1)|Caractère non valide (n’importe quelle valeur, à l’exception de 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|

## <a name="remarks"></a>Notes

La fonction **_mbbtype** détermine le type d’un octet dans un caractère multioctet. Si la valeur de *type* est toute valeur sauf 1, **_mbbtype** teste un octet codé sur un octet ou un octet de tête valide d’un caractère multioctet. Si la valeur de *type* est 1, **_mbbtype** teste un octet de fin valide d’un caractère multioctet.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . La version **_mbbtype** de cette fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version de **_mbbtype_l** est identique, à ceci près qu’elle utilise à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions antérieures, **_mbbtype** s’appelait **chkctype**. Pour le nouveau code, utilisez **_mbbtype** à la place.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les définitions des constantes manifestes utilisées comme valeurs de retour.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
