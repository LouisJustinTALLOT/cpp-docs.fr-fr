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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 85db4e478b070823bb14028018d918e0f3cabbd7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920318"
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
Rempli avec le nombre d’octets copiés (1 ou 2 en cas de réussite). Transmettez la **valeur null** si vous ne vous souciez pas du nombre.

*src*<br/>
Caractère multioctet à copier.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Si *src* ou *dest* a la **valeur null**, ou si plus de **buffSizeinBytes** octets sont copiés vers *dest*, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et **errno** a la valeur **EINVAL**.

## <a name="remarks"></a>Notes 

La fonction **_mbccpy_s** copie un caractère multioctet de *src* vers *dest*. Si *src* ne pointe pas vers l’octet de tête d’un caractère multioctet comme déterminé par un appel implicite à [_ismbblead](ismbblead-ismbblead-l.md), alors le seul octet vers lequel pointe *src* est copié. Si *src* pointe vers un octet de tête, mais que l’octet suivant est 0 et donc non valide, 0 est copié vers *dest*, **errno** a la valeur **EILSEQ**et la fonction retourne **EILSEQ**.

**_mbccpy_s** n’ajoute pas de terminateur null ; Toutefois, si *src* pointe vers un caractère null, alors cette valeur null est copiée vers *dest* (il s’agit simplement d’une copie sur un octet standard).

La valeur de *pCopied* est remplie avec le nombre d’octets copiés. Les valeurs possibles sont 1 et 2 si l’opération réussit. Si la **valeur null** est passée, ce paramètre est ignoré.

|*src*|copié vers *dest* .|*pCopied*|Valeur retournée|
|-----------|----------------------|---------------|------------------|
|Octet autre qu’un octet de tête|Octet autre qu’un octet de tête|1|0|
|0|0|1|0|
|Octet de tête suivi d’une valeur différente de 0|Octet de tête suivi d’une valeur différente de 0|2|0|
|Octet de tête suivi de 0|0|1|**EILSEQ**|

Notez que la deuxième ligne est simplement un cas spécial de la première. Notez également que le tableau suppose que *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux. **_mbccpy_s_l** est identique à **_mbccpy_s** sauf que **_mbccpy_s_l** utilise les paramètres régionaux passés pour tout comportement dépendant des paramètres régionaux.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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

[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multioctets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
