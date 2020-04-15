---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: aabe7e7c2e44f558b936e0fd4c6fa4a85dc582f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362968"
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

*strSource (en)*<br/>
Chaîne source.

*count*<br/>
Nombre maximum de caractères à placer dans *strDest*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne la longueur de la chaîne transformée, sans compter le caractère null de fin. Si la valeur de retour est supérieure ou égale à *compter,* le contenu de *strDest* est imprévisible. Sur une erreur, chaque fonction définit **errno** et retourne **INT_MAX**. Pour un caractère invalide, **errno** est réglé sur **EILSEQ**.

## <a name="remarks"></a>Notes

La fonction **strxfrm** transforme la chaîne pointée par *strSource* en une nouvelle forme collée qui est stockée dans *strDest*. Pas plus que *compter* les caractères, y compris le caractère nul, sont transformés et placés dans la chaîne résultante. La transformation se fait en utilisant le cadre de la catégorie **LC_COLLATE** de la région. Pour plus d’informations sur **LC_COLLATE**, voir [setlocale](setlocale-wsetlocale.md). **strxfrm** utilise le lieu actuel pour son comportement local-dépendant; **_strxfrm_l** est identique, sauf qu’il utilise le lieu passé au lieu de la localisation actuelle. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Après la transformation, un appel à **la strcmp** avec les deux cordes transformées donne des résultats identiques à ceux d’un appel à **strcoll** appliqué sur les deux cordes d’origine. Comme avec **strcoll** et **stricoll**, **strxfrm** gère automatiquement les cordes multioctets-caractères le cas échéant.

**wcsxfrm** est une version à caractère large de **strxfrm;** les arguments de cordes de **wcsxfrm** sont des pointeurs de caractère large. Pour **wcsxfrm**, après la transformation de la chaîne, un appel à **wcscmp** avec les deux cordes transformées donne des résultats identiques à ceux d’un appel à **wcscoll** appliqué sur les deux cordes d’origine. **wcsxfrm** et **strxfrm** se comportent de façon identique autrement. **wcsxfrm** utilise le lieu actuel pour son comportement local-dépendant; **_wcsxfrm_l** utilise le lieu passé au lieu de la localisation actuelle.

Ces fonctions valident leurs paramètres. Si *strSource* est un pointeur nul, ou *strDest* est un pointeur **NULL** (sauf si le nombre est nul), ou si le *nombre* est plus élevé que **INT_MAX**, le gestionnaire de paramètres invalides est invoqué, comme décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et le retour **INT_MAX**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Dans les paramètres régionaux "C", l'ordre des caractères dans le jeu de caractères (jeu de caractères ASCII) est le même que l'ordre lexicographique des caractères. Toutefois, dans d'autres paramètres régionaux, l'ordre des caractères dans le jeu de caractères peut différer de l'ordre des caractères lexicographiques. Par exemple, dans certains lieux européens, le personnage 'a' (valeur 0x61) \#précède le personnage '&x00E4;' (valeur 0xE4) dans l’ensemble de caractères, mais le personnage ''' précède le personnage 'a' lexicographically.

Dans les endroits pour lesquels le jeu de caractère et l’ordre de caractère lexicographique diffèrent, utilisez **le strxfrm** sur les cordes d’origine, puis **strcmp** sur les cordes résultantes pour produire une comparaison de chaîne lexicographique selon le cadre **de la** catégorie LC_COLLATE de la section actuelle. Ainsi, pour comparer deux cordes lexicographiquement dans le lieu ci-dessus, utilisez **le strxfrm** sur les cordes d’origine, puis **strcmp** sur les cordes résultantes. Alternativement, vous pouvez utiliser **strcoll** plutôt que **de strcmp** sur les cordes d’origine.

**strxfrm** est essentiellement un emballage autour [de LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) avec **LCMAP_SORTKEY**.

La valeur de l’expression suivante est la taille du tableau nécessaire pour tenir la transformation **strxfrm** de la chaîne source:

`1 + strxfrm( NULL, string, 0 )`

Dans le lieu "C" seulement, **strxfrm** est équivalent à ce qui suit:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Spécifications

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
[Local](../../c-runtime-library/locale.md)<br/>
[Manipulation des cordes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
