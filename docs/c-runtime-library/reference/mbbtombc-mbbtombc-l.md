---
title: _mbbtombc, _mbbtombc_l
ms.date: 4/2/2020
api_name:
- _mbbtombc_l
- _mbbtombc
- _o__mbbtombc
- _o__mbbtombc_l
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
ms.openlocfilehash: 5d26b06da1dcf8c53abda5d4ff2ee06ec3e7cd11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341415"
---
# <a name="_mbbtombc-_mbbtombc_l"></a>_mbbtombc, _mbbtombc_l

Convertit un caractère multioctet codé sur un octet en caractère multioctet codé sur deux octets correspondant.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Caractère codé sur un octet à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Si **_mbbtombc** convertit avec succès *c,* il renvoie un caractère multioctets; sinon, il retourne *c*.

## <a name="remarks"></a>Notes

La fonction **_mbbtombc** convertit un caractère multioctet unique donné en un caractère multioctet double-byte correspondant. Les caractères doivent être dans la plage 0x20 - 0x7E ou 0xA1 - 0xDF à convertir.

La valeur de sortie est affectée par l’établissement de la **LC_CTYPE’établissement** de la catégorie du lieu; voir [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de cette fonction sont identiques, sauf que **_mbbtombc** utilise le lieu actuel pour ce comportement local-dépendant et **_mbbtombc_l** utilise plutôt le paramètre local qui est passé dedans. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans les versions précédentes, **_mbbtombc** a été nommé **hantozen**. Pour un nouveau code, utilisez **_mbbtombc**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
