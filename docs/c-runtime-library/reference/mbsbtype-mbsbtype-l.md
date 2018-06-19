---
title: _mbsbtype, _mbsbtype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be098cb1fe53e1345f0c4f40212657f4bfd97f4f
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451017"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

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
|**_MBC_SINGLE** (0)|Caractère codé sur un octet. Par exemple, dans la page de codes 932, **_mbsbtype** retourne 0 si l’octet spécifié est dans la plage 0 x 20 – 0x7E ou 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Octet de tête de caractère multioctet. Par exemple, dans la page de codes 932, **_mbsbtype** retourne 1 si l’octet spécifié est dans la plage 0 x 81-0x9F ou 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Octet de fin de caractère multioctet. Par exemple, dans la page de codes 932, **_mbsbtype** renvoie la valeur 2 si l’octet spécifié est dans la plage 0 x 40-0x7E ou 0 x 80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**NULL** chaîne, un caractère non valide ou octet null trouvée avant l’octet au décalage *nombre* dans *mbstr*.|

## <a name="remarks"></a>Notes

Le **_mbsbtype** fonction détermine le type d’un octet dans une chaîne de caractères multioctets. La fonction examine uniquement les octets au décalage *nombre* dans *mbstr*, en ignorant les caractères non valides avant l’octet spécifié.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). La version de cette fonction sans le **_l** suffixe utilise les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux ; la version avec le **_l** suffixe est identique, sauf qu’il utilise les paramètres régionaux transmis dans à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si la chaîne d’entrée est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_MBC_ILLEGAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Pour les constantes manifestes utilisées comme valeurs de retour.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
