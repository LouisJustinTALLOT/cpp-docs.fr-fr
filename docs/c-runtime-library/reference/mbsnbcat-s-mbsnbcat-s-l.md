---
title: '`_mbsnbcat_s`, `_mbsnbcat_s_l`'
description: Description de l’API pour les `_mbsnbcat_s` fonctions Microsoft Visual C++ et `_mbsnbcat_s_l`
ms.date: 12/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c7198d806d8ebe077b423ff2135b5bdcf66ffac6
ms.sourcegitcommit: 9c45483572db4470fe5db5a7b596d5770303098c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96523112"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>`_mbsnbcat_s`, `_mbsnbcat_s_l`

Ajoute à une chaîne de caractères multioctets, au plus, les **n** premiers octets d’une autre chaîne de caractères multioctets. Il s’agit de versions de [ `_mbsnbcat` , `_mbsnbcat_l` ](mbsnbcat-mbsnbcat-l.md) qui ont des améliorations de sécurité, comme décrit dans [fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*`dest`*\
Chaîne de destination à caractères multioctets se terminant par un caractère null.

*`sizeInBytes`*\
Taille de la *`dest`* mémoire tampon en octets.

*`src`*\
Chaîne source à caractères multioctets se terminant par un caractère null.

*`count`*\
Nombre d’octets de *`src`* à ajouter à *`dest`* .

*`locale`*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Zéro en cas de réussite ; code d'erreur dans un autre cas.

### <a name="error-conditions"></a>Conditions d'erreur

|**`dest`**|*`sizeInBytes`*|*`src`*|Valeur retournée|
|------------|-------------------|-----------|------------------|
|**`NULL`**|n'importe laquelle|n'importe laquelle|**`EINVAL`**|
|Quelconque|<= 0|n'importe laquelle|**`EINVAL`**|
|Quelconque|n'importe laquelle|**`NULL`**|**`EINVAL`**|

Si l’une des conditions d’erreur se produit, la fonction génère une erreur de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction retourne **`EINVAL`** et définit **errno** sur **`EINVAL`** .

## <a name="remarks"></a>Notes

La **`_mbsnbcat_s`** fonction ajoute à *`dest`* , au plus, les premiers *`count`* octets de *`src`* . Si l’octet qui précède immédiatement le caractère NULL dans *`dest`* est un octet de tête, il est remplacé par l’octet initial de *`src`* . Dans le cas contraire, l’octet initial de *`src`* remplace le caractère null de fin de *`dest`* . Si un octet NULL apparaît dans *`src`* avant *`count`* l’ajout des octets, **`_mbsnbcat_s`** ajoute tous les octets de *`src`* , jusqu’au caractère null. Si *`count`* est supérieur à la longueur de *`src`* , la longueur de *`src`* est utilisée à la place de *`count`* . La chaîne obtenue se termine par un caractère null. Si la copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

La valeur de sortie est affectée par la valeur du **`LC_CTYPE`** paramètre de catégorie des paramètres régionaux. pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . Les versions de ces fonctions sont identiques, sauf que celles qui n’ont pas le **`_l`** suffixe utilisent les paramètres régionaux actuels et celles qui ont le **`_l`** suffixe utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle. Les surcharges peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui élimine la nécessité de spécifier un argument de taille, et elles peuvent utiliser automatiquement leurs fonctions plus récentes et plus sûres pour remplacer les fonctions plus anciennes et moins sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [`_CrtSetDebugFillThreshold`](crtsetdebugfillthreshold.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|`Tchar.h` simple|`_UNICODE` et `_MBCS` non défini|`_MBCS` définies|`_UNICODE` définies|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**`_tcsncat_s`**|[strncat_s](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|**`_mbsnbcat_s`**|[wcsncat_s](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|
|**`_tcsncat_s_l`**|**`_strncat_s_l`**|**`_mbsnbcat_s_l`**|**`_wcsncat_s_l`**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**`_mbsnbcat_s`**|\<mbstring.h>|
|**`_mbsnbcat_s_l`**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)\
[`_mbsnbcmp`, `_mbsnbcmp_l`](mbsnbcmp-mbsnbcmp-l.md)\
[`_strncnt`, `_wcsncnt`, `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt`, `_mbsnccnt_l`](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)\
[`_mbsnbcpy`, `_mbsnbcpy_l`](mbsnbcpy-mbsnbcpy-l.md)\
[`_mbsnbcpy_s`, `_mbsnbcpy_s_l`](mbsnbcpy-s-mbsnbcpy-s-l.md)\
[`_mbsnbset`, `_mbsnbset_l`](mbsnbset-mbsnbset-l.md)\
[`strncat`, `_strncat_l`, `wcsncat`, `_wcsncat_l`, `_mbsncat`, `_mbsncat_l`](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)\
[`strncat_s`, `_strncat_s_l`, `wcsncat_s`, `_wcsncat_s_l`, `_mbsncat_s`, `_mbsncat_s_l`](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)
