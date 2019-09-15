---
title: mbsrtowcs_s
ms.date: 11/04/2016
api_name:
- mbsrtowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: d79cceaf923c1da126a1d133a8d2eb8752883457
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952101"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Convertir une chaîne de caractères multioctets correspondant aux paramètres régionaux actuels en sa représentation sous forme de chaîne de caractères larges. Version de [mbsrtowcs](mbsrtowcs.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*pReturnValue*<br/>
Nombre de caractères convertis.

*wcstr*<br/>
Adresse de la mémoire tampon où stocker la chaîne de caractères larges convertie.

*sizeInWords*<br/>
Taille de *wcstr* en mots (caractères larges).

*mbstr*<br/>
Pointeur indirect vers l'emplacement de la chaîne de caractères multioctets à convertir.

*count*<br/>
Nombre maximal de caractères larges à stocker dans la mémoire tampon *wcstr* , à l’exclusion de la valeur null de fin ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Pointeur vers un objet d’état de conversion **mbstate_t** . Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Étant donné que l’objet **mbstate_t** interne n’est pas thread-safe, nous vous recommandons de toujours passer votre propre paramètre *mbstate* .

## <a name="return-value"></a>Valeur de retour

Zéro si la conversion est réussie, ou un code d'erreur en cas d'échec.

|Condition d'erreur|Valeur de retour et **errno**|
|---------------------|------------------------------|
|*wcstr* est un pointeur null et *sizeInWords* > 0|**EINVAL**|
|*mbstr* est un pointeur null|**EINVAL**|
|La chaîne indirectement pointée par *mbstr* contient une séquence multioctet qui n’est pas valide pour les paramètres régionaux actuels.|**EILSEQ**|
|La mémoire tampon de destination est trop petite pour contenir la chaîne convertie (à moins que *Count* ne soit **_TRUNCATE**; pour plus d’informations, consultez la section Notes).|**ERANGE**|

Si l’une de ces conditions se produit, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **mbsrtowcs_s** convertit une chaîne de caractères multioctets indirectement pointée par *mbstr* en caractères larges stockés dans la mémoire tampon pointée par *wcstr*, en utilisant l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère multioctet de null est rencontré.

- Un caractère multioctet non valide est rencontré.

- Le nombre de caractères larges stockés dans la mémoire tampon *wcstr* est égal à *Count*.

La chaîne de destination *wcstr* se termine toujours par un caractère null, même en cas d’erreur, sauf si *wcstr* est un pointeur null.

Si *Count* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** convertit la plus grande partie de la chaîne telle qu’elle est contenue dans la mémoire tampon de destination, tout en laissant de l’espace pour une marque de fin null.

Si **mbsrtowcs_s** convertit correctement la chaîne source, elle place la taille en caractères larges de la chaîne convertie et la marque de fin null dans  *&#42;pReturnValue*, à condition que *pReturnValue* ne soit pas un pointeur null. Cela se produit même si l’argument *wcstr* est un pointeur null et vous permet de déterminer la taille de mémoire tampon requise. Notez que si *wcstr* est un pointeur null, *Count* est ignoré.

Si *wcstr* n’est pas un pointeur null, l’objet pointeur désigné par *mbstr* reçoit un pointeur null si la conversion s’est arrêtée, car un caractère null de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si *mbstate* est un pointeur null, l’objet statique d’état de conversion **mbstate_t** interne de la bibliothèque est utilisé. Comme cet objet statique interne n’est pas thread-safe, nous vous recommandons de passer votre propre valeur *mbstate* .

Si **mbsrtowcs_s** rencontre un caractère multioctet qui n’est pas valide dans les paramètres régionaux actuels, il place-1 dans  *&#42;pReturnValue*, définit la mémoire tampon de destination *wcstr* sur une chaîne vide, affecte à **errno** la valeur **EILSEQ**et retourne **EILSEQ**.

Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbsrtowcs_s** n’est pas défini. **mbsrtowcs_s** est affecté par la catégorie LC_TYPE des paramètres régionaux actuels.

> [!IMPORTANT]
> Assurez-vous que *wcstr* et *mbstr* ne se chevauchent pas, et que ce *nombre* reflète correctement le nombre de caractères multioctets à convertir.

La fonction **mbsrtowcs_s** diffère de [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) par son redémarrage. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application doit utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs_s** est utilisé à la place de **mbstowcs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et elles peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

La fonction **mbsrtowcs_s** est multithread safe si aucune fonction du thread actif n’appelle **setlocale** tant que cette fonction est en cours d’exécution et que l’argument *mbstate* n’est pas un pointeur null.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
