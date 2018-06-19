---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc9746d2c98f1799cbdd244e7fc4d465fd705fa
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451717"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

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

Retourne la longueur de la chaîne transformée, sans compter le caractère null de fin. Si la valeur de retour est supérieure ou égale à *nombre*, le contenu de *strDest* est imprévisible. En cas d’erreur, chaque fonction définit **errno** et retourne **INT_MAX**. Un caractère non valide, **errno** a la valeur **EILSEQ**.

## <a name="remarks"></a>Notes

Le **strxfrm** fonction transforme la chaîne pointée par *strSource* dans un nouveau format assemblé qui est stocké dans *strDest*. Pas plus de *nombre* caractères, y compris le caractère null, sont transformés et placés dans la chaîne résultante. La transformation s’effectue à l’aide de paramètres régionaux **LC_COLLATE** paramètre de catégorie. Pour plus d’informations sur **LC_COLLATE**, consultez [setlocale](setlocale-wsetlocale.md). **strxfrm** utilise les paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux ; **_strxfrm_l** est identique, sauf qu’elle utilise les paramètres régionaux passé au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Après la transformation, un appel à **strcmp** avec les deux chaînes transformées génère des résultats identiques à ceux d’un appel à **strcoll** appliqué aux deux chaînes d’origine. Comme avec **strcoll** et **stricoll**, **strxfrm** gère automatiquement les chaînes de caractères multioctets selon le cas.

**wcsxfrm** est une version à caractères larges de **strxfrm**; les arguments de chaîne de **wcsxfrm** sont des pointeurs à caractères larges. Pour **wcsxfrm**, après la transformation de chaîne, un appel à **wcscmp** avec les deux chaînes transformées génère des résultats identiques à ceux d’un appel à **wcscoll** appliquée à la deux chaînes d’origine. **wcsxfrm** et **strxfrm** comportent de façon identique. **wcsxfrm** utilise les paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux ; **_wcsxfrm_l** utilise les paramètres régionaux passé au lieu des paramètres régionaux actuels.

Ces fonctions valident leurs paramètres. Si *strSource* est un pointeur null, ou *strDest* est un **NULL** pointeur (sauf si le nombre est égal à zéro), ou si *nombre* est supérieur à **INT_MAX**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Dans les paramètres régionaux "C", l'ordre des caractères dans le jeu de caractères (jeu de caractères ASCII) est le même que l'ordre lexicographique des caractères. Toutefois, dans d'autres paramètres régionaux, l'ordre des caractères dans le jeu de caractères peut différer de l'ordre des caractères lexicographiques. Par exemple, dans certains paramètres régionaux européens, le caractère « a » (valeur 0 x 61) précède le caractère ' &\#x00E4 ;' (valeur 0xE4) dans le jeu de caractères, mais le caractère « ä » précède le caractère 'a' lexicographique.

Dans les paramètres régionaux pour lesquels le jeu de caractères et l’ordre lexicographique des caractères diffèrent, utilisez **strxfrm** sur les chaînes d’origine, puis **strcmp** sur les chaînes résultantes pour produire une chaîne lexicographique comparaison selon les paramètres régionaux actuels **LC_COLLATE** paramètre de catégorie. Par conséquent, pour comparer deux chaînes lexicographiquement dans les paramètres régionaux ci-dessus, utilisez **strxfrm** sur les chaînes d’origine, puis **strcmp** sur les chaînes résultantes. Vous pouvez également utiliser **strcoll** plutôt que **strcmp** sur les chaînes d’origine.

**strxfrm** est essentiellement un wrapper autour de [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) avec **LCMAP_SORTKEY**.

La valeur de l’expression suivante est la taille du tableau nécessaire pour contenir le **strxfrm** transformation de la chaîne source :

`1 + strxfrm( NULL, string, 0 )`

Dans les paramètres régionaux « C » uniquement, **strxfrm** est équivalente à la suivante :

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
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
