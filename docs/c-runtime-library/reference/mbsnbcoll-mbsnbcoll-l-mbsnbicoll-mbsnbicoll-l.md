---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
dev_langs:
- C++
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19e17552a674d4931134eb9d7b436a0f858843d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405391"
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Compare *n* octets de deux chaînes de caractères multioctets en utilisant les informations de la page de codes multioctets.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*string1*, *chaîne2*<br/>
Chaînes à comparer.

*count*<br/>
Nombre d'octets à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation entre les sous-chaînes de *string1* et *chaîne2*.

|Valeur de retour|Description|
|------------------|-----------------|
|< 0|*string1* sous-chaîne moins *chaîne2* sous-chaîne.|
|0|*string1* sous-chaîne identique à *chaîne2* sous-chaîne.|
|> 0|*string1* sous-chaîne supérieur *chaîne2* sous-chaîne.|

Si *string1* ou *chaîne2* est **NULL** ou *nombre* est supérieur à **INT_MAX**, non valide Gestionnaire de paramètres est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et **errno** à **EINVAL**. Pour utiliser **_NLSCMPERROR**, incluez String.h ou Mbstring.h.

## <a name="remarks"></a>Notes

Chacune de ces fonctions assemble au maximum, la première *nombre* octets *string1* et *chaîne2* et retourne une valeur qui indique la relation entre résultant les sous-chaînes de *string1* et *chaîne2*. Si le dernier octet de la sous-chaîne de *string1* ou *chaîne2* est un octet de tête, il n’est pas inclus dans la comparaison ; ces fonctions comparer uniquement des caractères dans les sous-chaînes terminées. **_mbsnbicoll** est une version de la casse de **_mbsnbcoll**. Comme [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) et [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** et **_mbsnbicoll** collate, les deux chaînes de caractères multioctets en fonction de la ordre lexicographique spécifié par le multioctets [page de codes](../../c-runtime-library/code-pages.md) en cours d’utilisation.

Pour certaines pages de codes et les jeux de caractères correspondants, l’ordre des caractères dans le jeu de caractères peut différer de l’ordre lexicographique des caractères. Dans les paramètres régionaux « C », ce n’est pas le cas : l’ordre des caractères dans le jeu de caractères ASCII est le même que l’ordre lexicographique des caractères. Cependant, dans certaines pages de code européennes, par exemple, le caractère « a » (valeur 0x61) précède le caractère « ä » (valeur 0xE4) dans le jeu de caractères, alors que d’un point de vue lexicographique, le caractère « ä » précède le caractère « a ». Pour effectuer une comparaison lexicographique de chaînes en octets dans ce cas, utilisez **_mbsnbcoll** plutôt que **_mbsnbcmp**; pour vérifier uniquement l’égalité de chaînes, utilisez **_mbsnbcmp**.

Parce que le **coll** fonctions collate chaînes lexicographiquement pour la comparaison, tandis que le **cmp** fonctions simplement testent l’égalité de chaîne, le **coll** sont des fonctions beaucoup plus lent que correspondant **cmp** versions. Par conséquent, le **coll** fonctions doivent être utilisées uniquement lorsqu’il existe une différence entre l’ordre du jeu de caractères et l’ordre lexicographique des caractères dans la page de codes actuelle cette différence présente un intérêt pour la comparaison.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
