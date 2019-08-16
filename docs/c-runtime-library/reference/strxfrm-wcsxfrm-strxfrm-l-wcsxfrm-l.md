---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: e4dc94d76562daf10544e9b0d09d9608bd83e454
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500783"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transforme une chaîne en fonction des informations spécifiques aux paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strDest*<br/>
Chaîne de destination.

*strSource*<br/>
Chaîne source.

*count*<br/>
Nombre maximal de caractères à placer dans *strDest*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne la longueur de la chaîne transformée, sans compter le caractère null de fin. Si la valeur de retour est supérieure ou égale à *Count*, le contenu de *strDest* est imprévisible. En cas d’erreur, chaque fonction définit **errno** et retourne **INT_MAX**. Pour un caractère non valide, **errno** a la valeur **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **strxfrm** transforme la chaîne pointée par *strSource* en un nouveau formulaire assemblé qui est stocké dans *strDest*. Au plus, le *nombre* de caractères, y compris le caractère null, sont transformés et placés dans la chaîne résultante. La transformation est effectuée à l’aide du paramètre de catégorie **LC_COLLATE** des paramètres régionaux. Pour plus d’informations sur **LC_COLLATE**, consultez [setlocale](setlocale-wsetlocale.md). **strxfrm** utilise les paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux; **_strxfrm_l** est identique, à ceci près qu’il utilise les paramètres régionaux passés au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Après la transformation, un appel à **strcmp** avec les deux chaînes transformées génère des résultats identiques à ceux d’un appel à **strcoll** appliqué aux deux chaînes d’origine. Comme avec **strcoll** et **stricoll**, **strxfrm** gère automatiquement les chaînes de caractères multioctets comme il convient.

**wcsxfrm** est une version à caractères larges de **strxfrm**; les arguments de chaîne de **wcsxfrm** sont des pointeurs à caractères larges. Pour **wcsxfrm**, après la transformation de chaîne, un appel à **wcscmp** avec les deux chaînes transformées génère des résultats identiques à ceux d’un appel à **wcscoll** appliqué aux deux chaînes d’origine. dans le cas contraire, **wcsxfrm** et **strxfrm** se comportent de la même façon. **wcsxfrm** utilise les paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux; **_wcsxfrm_l** utilise les paramètres régionaux passés au lieu des paramètres régionaux actuels.

Ces fonctions valident leurs paramètres. Si *strSource* est un pointeur null ou si *strDest* est un pointeur **null** (sauf si Count est égal à zéro) ou si le *nombre* est supérieur à **INT_MAX**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Dans les paramètres régionaux "C", l'ordre des caractères dans le jeu de caractères (jeu de caractères ASCII) est le même que l'ordre lexicographique des caractères. Toutefois, dans d'autres paramètres régionaux, l'ordre des caractères dans le jeu de caractères peut différer de l'ordre des caractères lexicographiques. Par exemple, dans certains paramètres régionaux européens, le caractère «a» (valeur 0x61) précède le caractère «&\#x00E4;» (valeur 0xE4) dans le jeu de caractères, mais le caractère «ä» précède le caractère «a» vue lexicographique.

Dans les paramètres régionaux pour lesquels le jeu de caractères et l’ordre des caractères lexicographique diffèrent, utilisez **strxfrm** sur les chaînes d’origine, puis **strcmp** sur les chaînes résultantes pour produire une comparaison de chaînes lexicographique en fonction des paramètres régionaux actuels Paramètre de catégorie **LC_COLLATE** . Ainsi, pour comparer deux chaînes vue lexicographique dans les paramètres régionaux ci-dessus, utilisez **strxfrm** sur les chaînes d’origine, puis **strcmp** sur les chaînes résultantes. Vous pouvez également utiliser **strcoll** plutôt que **strcmp** sur les chaînes d’origine.

**strxfrm** est fondamentalement un wrapper autour de [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) avec **LCMAP_SORTKEY**.

La valeur de l’expression suivante est la taille du tableau nécessaire pour contenir la transformation **strxfrm** de la chaîne source:

`1 + strxfrm( NULL, string, 0 )`

Dans les paramètres régionaux «C» uniquement, **strxfrm** est équivalent à ce qui suit:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> ou \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
