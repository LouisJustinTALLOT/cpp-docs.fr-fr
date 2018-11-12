---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
apiname:
- _mbbtype
- _mbbtype_l
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
ms.openlocfilehash: a6d17b99e4314c2ab836a16129ab8a0e6ac7720e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467169"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l

Retourne le type d'octet en se basant sur l'octet précédent.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

## <a name="return-value"></a>Valeur de retour

**_mbbtype** retourne le type d’octet dans une chaîne. Cette décision tient compte, comme spécifié par la valeur de *type*, qui fournit la condition de test du contrôle. *type* est le type de l’octet précédent dans la chaîne. Les constantes manifestes présentes dans le tableau suivant sont définies dans Mbctype.h.

|Valeur de *type*|**_mbbtype** pour les tests|Valeur de retour|*c*|
|---------------------|--------------------------|------------------|---------|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_SINGLE** (0)|Octet unique (0 x 20 - 0x7E, 0xA1 - 0xDF)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_LEAD** (1)|Octet de caractère multioctet tête (0 x 81 - 0x9F, 0xE0 - 0xFC)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_ILLEGAL**<br /><br /> ( -1)|Caractère non valide (toute valeur sauf 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|
|1|Octet de fin valide|**_MBC_TRAIL** (2)|Octet de caractère multioctet fin (0 x 40 - 0x7E, 0 x 80 - 0xFC)|
|1|Octet de fin valide|**_MBC_ILLEGAL**<br /><br /> ( -1)|Caractère non valide (toute valeur sauf 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Notes

Le **_mbbtype** fonction détermine le type d’un octet dans un caractère multioctet. Si la valeur de *type* est n’importe quelle valeur sauf 1, **_mbbtype** tests pour un valid un octet ou octet de tête d’un caractère multioctet. Si la valeur de *type* est 1, **_mbbtype** tests pour un octet de fin valide d’un caractère multioctet.

La valeur de sortie est affectée par la valeur de la **LC_CTYPE** catégorie des paramètres régionaux ; consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Le **_mbbtype** version de cette fonction utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la **_mbbtype_l** version est identique, à ceci près qu’elle utilise les paramètres régionaux qui sont passés à la place . Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions antérieures, **_mbbtype** s’appelait **chkctype**. Pour le nouveau code, utilisez **_mbbtype** à la place.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les définitions des constantes manifestes utilisées comme valeurs de retour.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
