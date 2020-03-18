---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 11/04/2016
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
- mbsnbcoll_l
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
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: d759bda0133a95406a586011d39d69074283bf97
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438208"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Compare *n* octets de deux chaînes de caractères multioctets à l’aide des informations de page de codes multioctets.

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

*Chaîne1*, *Chaîne2*<br/>
Chaînes à comparer.

*count*<br/>
Nombre d'octets à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

La valeur de retour indique la relation des sous-chaînes de *Chaîne1* et *Chaîne2*.

|Valeur retournée|Description|
|------------------|-----------------|
|< 0|*Chaîne1* sous-chaîne inférieure à *Chaîne2* sous-chaîne.|
|0|*Chaîne1* sous-chaîne identique à la sous-chaîne *Chaîne2* .|
|> 0|*Chaîne1* SUBSTRING supérieure à la sous-chaîne *Chaîne2* .|

Si *Chaîne1* ou *Chaîne2* a la **valeur null** ou si le *nombre* est supérieur à **INT_MAX**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et attribuent à **errno** la valeur **EINVAL**. Pour utiliser **_NLSCMPERROR**, incluez String. h ou mbstring. h.

## <a name="remarks"></a>Notes

Chacune de ces fonctions rassemble, au plus, le premier *nombre* d’octets dans *Chaîne1* et *Chaîne2* et retourne une valeur indiquant la relation entre les sous-chaînes résultantes de *string1* et *string2*. Si le dernier octet de la sous-chaîne de *string1* ou *string2* est un octet de tête, il n’est pas inclus dans la comparaison ; ces fonctions comparent uniquement les caractères complets dans les sous-chaînes. **_mbsnbicoll** est une version de **_mbsnbcoll**qui ne respecte pas la casse. Comme [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) et [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** et **_mbsnbicoll** classent les deux chaînes de caractères multioctets en fonction de l’ordre lexicographique spécifié par la [page de codes](../../c-runtime-library/code-pages.md) multioctets en cours d’utilisation.

Pour certaines pages de codes et les jeux de caractères correspondants, l’ordre des caractères dans le jeu de caractères peut différer de l’ordre lexicographique des caractères. Dans les paramètres régionaux « C », ce n’est pas le cas : l’ordre des caractères dans le jeu de caractères ASCII est le même que l’ordre lexicographique des caractères. Cependant, dans certaines pages de code européennes, par exemple, le caractère « a » (valeur 0x61) précède le caractère « ä » (valeur 0xE4) dans le jeu de caractères, alors que d’un point de vue lexicographique, le caractère « ä » précède le caractère « a ». Pour effectuer une comparaison lexicographique de chaînes par octets dans une telle instance, utilisez **_mbsnbcoll** plutôt que **_mbsnbcmp**; pour vérifier uniquement l’égalité des chaînes, utilisez **_mbsnbcmp**.

Étant donné que les fonctions **coll** rassemblent les chaînes vue lexicographique à des fins de comparaison, tandis que les fonctions **CMP** testent simplement l’égalité des chaînes, les fonctions **coll** sont beaucoup plus lentes que les versions **CMP** correspondantes. Par conséquent, les fonctions **coll** ne doivent être utilisées que s’il existe une différence entre l’ordre du jeu de caractères et l’ordre des caractères lexicographique dans la page de codes actuelle, et si cette différence présente un intérêt pour la comparaison.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis. Pour plus d'informations, consultez [Locale](../../c-runtime-library/locale.md).

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

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
