---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341235"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Copier un caractère multioctet d’une chaîne vers une autre chaîne. Ces versions de [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Destination de la copie.

*buffSizeInBytes*<br/>
Taille de la mémoire tampon de destination.

*pCopied*<br/>
Rempli avec le nombre d’octets copiés (1 ou 2 en cas de réussite). Passez **NULL** si vous ne vous souciez pas du numéro.

*src*<br/>
Caractère multioctet à copier.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Si *le cr* ou le *dest* est **NULL**, ou si plus de **buffSizeinBytes octets** seraient copiés pour *dest*, alors le gestionnaire de paramètre invalide est invoqué, comme décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et **errno** est réglé à **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_mbccpy_s** copie un personnage multioctet de *src* à *dest*. Si *le src* ne pointe pas vers le byte de plomb d’un caractère multioctet tel que déterminé par un appel implicite à [_ismbblead](ismbblead-ismbblead-l.md), alors le byte unique qui *src* pointe à est copié. Si *src* pointe vers un byte de plomb mais que le byte suivant est de 0 et donc invalide, alors 0 est copié pour *dest*, **errno** est réglé sur **EILSEQ**, et la fonction **renvoie EILSEQ**.

**_mbccpy_s** n’appende pas un terminateur nul; cependant, si *src* pointe vers un caractère nul, alors ce null est copié pour *dest* (ce n’est qu’une copie régulière d’un seul-byte).

La valeur en *pCopied* est remplie du nombre d’octets copiés. Les valeurs possibles sont 1 et 2 si l’opération réussit. Si **NULL** est passé, ce paramètre est ignoré.

|*src*|copié pour *dest*|*pCopied*|Valeur retournée|
|-----------|----------------------|---------------|------------------|
|Octet autre qu’un octet de tête|Octet autre qu’un octet de tête|1|0|
|0|0|1|0|
|Octet de tête suivi d’une valeur différente de 0|Octet de tête suivi d’une valeur différente de 0|2|0|
|Octet de tête suivi de 0|0|1|**EILSEQ**|

Notez que la deuxième ligne est simplement un cas spécial de la première. Notez également que la table suppose *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** utilise le lieu actuel pour tout comportement local-dépendant. **_mbccpy_s_l** est identique à **_mbccpy_s** sauf que **_mbccpy_s_l** utilise le lieu passé pour tout comportement local-dépendant.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Mappe à la macro ou à la fonction inline.|**_mbccpy_s**|Mappe à la macro ou à la fonction inline.|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
