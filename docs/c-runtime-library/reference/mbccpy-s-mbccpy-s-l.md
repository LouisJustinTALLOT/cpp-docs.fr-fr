---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
ms.openlocfilehash: f9a7554630bd3b46196358c01c21b99978c53e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575043"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l

Copier un caractère multioctet d’une chaîne vers une autre chaîne. Ces versions de [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Rempli avec le nombre d’octets copiés (1 ou 2 en cas de réussite). Passer **NULL** si le nombre ne vous intéressent.

*src*<br/>
Caractère multioctet à copier.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec. Si *src* ou *dest* est **NULL**, ou si plusieurs **buffSizeinBytes** octets sont copiés à *dest*, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions retournent **EINVAL** et **errno** a la valeur **EINVAL**.

## <a name="remarks"></a>Notes

Le **_mbccpy_s** fonction copie un caractère multioctet depuis *src* à *dest*. Si *src* ne pointe pas vers l’octet de tête d’un caractère multioctet comme déterminé par un appel implicite à [_ismbblead](ismbblead-ismbblead-l.md), puis l’octet unique qui *src* est copié. Si *src* pointe vers un octet de tête, mais l’octet suivant est 0 et donc non valide, 0 est copié vers *dest*, **errno** a la valeur **EILSEQ**et le fonction renvoie **EILSEQ**.

**_mbccpy_s** n’ajoute pas d’une marque de fin null ; Cependant, si *src* pointe vers un caractère null, cette valeur null est copié vers *dest* (c’est juste une copie d’un octet normale).

La valeur dans *pCopied* est rempli avec le nombre d’octets copiés. Les valeurs possibles sont 1 et 2 si l’opération réussit. Si **NULL** est passée, ce paramètre est ignoré.

|*src*|copié dans *dest*|*pCopied*|Valeur de retour|
|-----------|----------------------|---------------|------------------|
|Octet autre qu’un octet de tête|Octet autre qu’un octet de tête|1|0|
|0|0|1|0|
|Octet de tête suivi d’une valeur différente de 0|Octet de tête suivi d’une valeur différente de 0|2|0|
|Octet de tête suivi de 0|0|1|**EILSEQ**|

Notez que la deuxième ligne est simplement un cas spécial de la première. Notez également que ce tableau suppose *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux. **_mbccpy_s_l** est identique à **_mbccpy_s** , à ceci près que **_mbccpy_s_l** utilise les paramètres régionaux passé pour n’importe quel comportement dépendant des paramètres régionaux.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Mappe à la macro ou à la fonction inline.|**_mbccpy_s**|Mappe à la macro ou à la fonction inline.|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
