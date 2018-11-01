---
title: _mbctombb, _mbctombb_l
ms.date: 11/04/2016
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
ms.openlocfilehash: 7395d94a6ec18f989d4a7153425b7af406a0bf45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519832"
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb, _mbctombb_l

Convertit un caractère multioctet codé sur deux octets en caractère multioctet codé sur un octet correspondant.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère multioctet à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_mbctombb** et **_mbctombb_l** retourne le caractère d’un octet qui correspond à *c*; sinon, elle retourne *c* .

## <a name="remarks"></a>Notes

Le **_mbctombb** et **_mbctombb_l** fonctions convertissent un caractère multioctet donné en un caractère multioctet codés sur un octet correspondant. Caractères doivent correspondre à caractères codés sur un octet dans la plage 0 x 20-0x7E ou 0xA1 - 0xDF à convertir.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version de cette fonction sans le **_l** suffixe utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version avec le **_l** suffixe est identique, à ceci près qu’elle utilise les paramètres régionaux passés dans à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions précédentes, **_mbctombb** a été appelée **zentohan**. Utilisez **_mbctombb** à la place.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbctombb**|\<mbstring.h>|
|**_mbctombb_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
