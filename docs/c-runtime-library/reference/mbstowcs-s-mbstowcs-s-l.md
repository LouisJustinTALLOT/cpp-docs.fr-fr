---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
api_name:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 0812c3f667f28c5c43d7932d4746052dbaff3a60
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952024"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Convertit une séquence de caractères multioctets en séquence correspondante de caractères larges. Versions de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) intégrant les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
Nombre de caractères convertis.

*wcstr*<br/>
Adresse de la mémoire tampon pour la chaîne de caractères larges convertie résultante.

*sizeInWords*<br/>
Taille de la mémoire tampon *wcstr* en mots.

*mbstr*<br/>
Adresse d’une séquence de caractères multioctets se terminant par un caractère Null.

*count*<br/>
Nombre maximal de caractères larges à stocker dans la mémoire tampon *wcstr* , à l’exclusion de la valeur null de fin ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi, un code d'erreur en cas d'échec.

|Condition d'erreur|Valeur de retour et **errno**|
|---------------------|------------------------------|
|*wcstr* a la **valeur NULL** et *sizeInWords* > 0|**EINVAL**|
|*mbstr* a la **valeur null**|**EINVAL**|
|La mémoire tampon de destination est trop petite pour contenir la chaîne convertie (sauf si *Count* est **_TRUNCATE**; consultez les remarques ci-dessous)|**ERANGE**|
|*wcstr* n’est pas **null** et *sizeInWords* = = 0|**EINVAL**|

Si l’une de ces conditions se présente, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **mbstowcs_s** convertit une chaîne de caractères multioctets pointée par *mbstr* en caractères larges stockés dans la mémoire tampon vers laquelle pointe *wcstr*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère multioctet de null est rencontré.

- Un caractère multioctet non valide est rencontré.

- Le nombre de caractères larges stockés dans la mémoire tampon *wcstr* est égal à *Count*.

La chaîne de destination est toujours terminée par null (même en cas d'erreur).

Si *Count* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), **mbstowcs_s** convertit le plus possible la chaîne telle qu’elle est contenue dans la mémoire tampon de destination, tout en laissant de l’espace pour une marque de fin null.

Si **mbstowcs_s** convertit correctement la chaîne source, elle place la taille en caractères larges de la chaîne convertie, y compris la marque de fin null, dans  *&#42;pReturnValue* (le *pReturnValue* fourni n’est pas **null**). Cela se produit même si l’argument *wcstr* est **null** et fournit un moyen de déterminer la taille de mémoire tampon requise. Notez que si *wcstr* a la **valeur null**, *Count* est ignoré et *sizeInWords* doit avoir la valeur 0.

Si **mbstowcs_s** rencontre un caractère multioctet non valide, il place 0 dans  *&#42;pReturnValue*, définit la mémoire tampon de destination sur une chaîne vide, définit **errno** sur **EILSEQ**et retourne **EILSEQ**.

Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbstowcs_s** n’est pas défini.

> [!IMPORTANT]
> Assurez-vous que *wcstr* et *mbstr* ne se chevauchent pas, et que ce *nombre* reflète correctement le nombre de caractères multioctets à convertir.

**mbstowcs_s** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; **_mbstowcs_s_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
