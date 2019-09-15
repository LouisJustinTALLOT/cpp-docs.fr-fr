---
title: _mbsbtype, _mbsbtype_l
ms.date: 11/04/2016
api_name:
- _mbsbtype_l
- _mbsbtype
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
ms.openlocfilehash: c474cad9027b7914a08816346e38e954a7200bb5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952393"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Retourne le type d’octet dans une chaîne.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

**_mbsbtype** et **_mbsbtype_l** retourne une valeur entière indiquant le résultat du test sur l’octet spécifié. Les constantes manifestes présentes dans le tableau suivant sont définies dans Mbctype.h.

|Valeur de retour|Type d’octet|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Caractère codé sur un octet. Par exemple, dans la page de codes 932, **_mbsbtype** retourne 0 si l’octet spécifié est compris dans la plage 0X20-0X7e ou 0XA1-0xDF.|
|**_MBC_LEAD** (1)|Octet de tête de caractère multioctet. Par exemple, dans la page de codes 932, **_mbsbtype** retourne 1 si l’octet spécifié se trouve dans la plage 0X81-0X9f ou 0XE0-0xFC.|
|**_MBC_TRAIL** (2)|Octet de fin de caractère multioctet. Par exemple, dans la page de codes 932, **_mbsbtype** retourne 2 si l’octet spécifié est compris dans la plage 0X40-0x7E ou 0X80-0xFC.|
|**_MBC_ILLEGAL** (-1)|Chaîne **null** , caractère non valide ou octet NULL trouvé avant le *nombre* d’octets au niveau du décalage dans *mbstr*.|

## <a name="remarks"></a>Notes

La fonction **_mbsbtype** détermine le type d’un octet dans une chaîne de caractères multioctets. La fonction examine uniquement le *nombre* d’octets au niveau du décalage dans *mbstr*, en ignorant les caractères non valides avant l’octet spécifié.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version de cette fonction sans le suffixe **_L** utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version avec le suffixe **_L** est identique, à ceci près qu’elle utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si la chaîne d’entrée est **null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_MBC_ILLEGAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les constantes manifestes utilisées comme valeurs de retour.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
