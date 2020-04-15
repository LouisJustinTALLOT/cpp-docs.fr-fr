---
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340872"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Retourne le type d’octet dans une chaîne.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*mbstr*<br/>
Adresse d’une séquence de caractères multioctets.

*count*<br/>
Décalage d’octet à partir du début de la chaîne.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_mbsbtype** et **_mbsbtype_l** renvoie une valeur d’intégrant indiquant le résultat du test sur le byte spécifié. Les constantes manifestes présentes dans le tableau suivant sont définies dans Mbctype.h.

|Valeur retournée|Type d’octet|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Caractère codé sur un octet. Par exemple, dans la page de code 932, **_mbsbtype** renvoie 0 si le byte spécifié se situe dans la plage 0x20 - 0x7E ou 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Octet de tête de caractère multioctet. Par exemple, dans la page de code 932, **_mbsbtype** renvoie 1 si le byte spécifié se situe dans la plage 0x81 - 0x9F ou 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Octet de fin de caractère multioctet. Par exemple, dans la page de code 932, **_mbsbtype** renvoie 2 si le byte spécifié se situe dans la plage 0x40 - 0x7E ou 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**NULL** string, caractère invalide, ou byte nul trouvé devant le byte au *compte* de compensation en *mbstr*.|

## <a name="remarks"></a>Notes

La fonction **_mbsbtype** détermine le type d’en-l’air dans une chaîne de caractères multioctets. La fonction n’examine que le byte au *nombre* de décalages dans *mbstr*, ignorant les caractères invalides avant le byte spécifié.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version de cette fonction sans le **suffixe _l** utilise le lieu actuel pour ce comportement local-dépendant; la version avec le **suffixe _l** est identique, sauf qu’elle utilise le paramètre local passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si la chaîne d’entrée est **NULL**, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et la fonction retourne **_MBC_ILLEGAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les constantes manifestes utilisées comme valeurs de retour.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
