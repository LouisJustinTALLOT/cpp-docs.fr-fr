---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341412"
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

*C*<br/>
Caractère à tester.

*type*<br/>
Type d'octet à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_mbbtype** retourne le type d’ense de fourre-tout dans une chaîne. Cette décision est sensible au contexte, comme le précise la valeur du *type,* qui fournit la condition de test de contrôle. *type* est le type de l’ente précédent dans la chaîne. Les constantes manifestes présentes dans le tableau suivant sont définies dans Mbctype.h.

|Valeur du *type*|**_mbbtype** tests pour|Valeur retournée|*C*|
|---------------------|--------------------------|------------------|---------|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_SINGLE** (0)|Single byte (0x20 - 0x7E, 0xA1 - 0xDF)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_LEAD** (1)|Byte de plomb de caractère multioctet (0x81 - 0x9F, 0xE0 - 0xFC)|
|Toute valeur sauf 1|Octet unique ou octet de tête valide|**_MBC_ILLEGAL**<br /><br /> ( -1)|Caractère invalide (toute valeur sauf 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|
|1|Octet de fin valide|**_MBC_TRAIL** (2)|Suivi byte de caractère multioctet (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Octet de fin valide|**_MBC_ILLEGAL**<br /><br /> ( -1)|Caractère invalide (toute valeur sauf 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Notes

La fonction **_mbbtype** détermine le type d’en-l’est dans un caractère multioctet. Si la valeur du *type* est une valeur à l’exception de 1, **_mbbtype** des tests pour un son unique ou un sous-lieu valide d’un caractère multioctet. Si la valeur du *type* est de 1, **_mbbtype** tests pour un byte de sentier valide d’un caractère multioctet.

La valeur de sortie est affectée par l’établissement de la **LC_CTYPE’établissement** de la catégorie du lieu; voir [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. La version **_mbbtype** de cette fonction utilise le lieu actuel pour ce comportement local-dépendant; la version **_mbbtype_l** est identique, sauf qu’elle utilise le paramètre local qui est passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions précédentes, **_mbbtype** a été nommé **chkctype**. Pour un nouveau code, utilisez **_mbbtype** à la place.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les définitions des constantes manifestes utilisées comme valeurs de retour.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
