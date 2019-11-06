---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 11/04/2016
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: a148f4be503ee793e4e36855233edfc8fa8f165a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624338"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Ajoute à une chaîne de caractères multioctets, au plus, les **n** premiers octets d’une autre chaîne de caractères multioctets. Il s’agit de versions de [_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) qui intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Chaîne de destination à caractères multioctets se terminant par un caractère null.

*sizeInBytes*<br/>
Taille de la mémoire tampon de *destination* en octets.

*src*<br/>
Chaîne source à caractères multioctets se terminant par un caractère null.

*count*<br/>
Nombre d’octets de *src* à ajouter à *dest*.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ; code d'erreur dans un autre cas.

### <a name="error-conditions"></a>Conditions d’erreur

|**Dest**|*sizeInBytes*|*src*|Valeur de retour|
|------------|-------------------|-----------|------------------|
|**NULL**|indifférent|indifférent|**EINVAL**|
|Any|<= 0|indifférent|**EINVAL**|
|Any|indifférent|**NULL**|**EINVAL**|

Si l’une des conditions d’erreur se produit, la fonction génère une erreur de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction retourne **EINVAL** et définit **errno** sur **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_mbsnbcat_s** ajoute à *dest*, au plus, le premier *nombre* d’octets de *src*. Si l’octet qui précède immédiatement le caractère NULL dans *dest* est un octet de tête, il est remplacé par l’octet initial de *src*. Dans le cas contraire, l’octet initial de *src* remplace le caractère null de fin de *dest*. Si un octet NULL apparaît dans *src* avant que le *nombre* d’octets soit ajouté, **_mbsnbcat_s** ajoute tous les octets de *src*, jusqu’au caractère null. Si *Count* est supérieur à la longueur de *src*, la longueur de *src* est utilisée à la place de *Count*. La chaîne obtenue se termine par un caractère null. Si la copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . Les versions de ces fonctions sont identiques, sauf que celles qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels et celles qui ont le suffixe **_L** utilisent à la place les paramètres régionaux qui sont passés. Pour plus d'informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement, ce qui évite ainsi d’avoir à spécifier un argument de taille, et elles peuvent utiliser automatiquement leurs fonctions plus récentes et plus sécurisées en remplacement des fonctions plus anciennes, moins sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
