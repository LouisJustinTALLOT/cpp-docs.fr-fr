---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338900"
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
La taille du *wcstr* en mots (caractères larges).

*mbstr*<br/>
Pointeur indirect vers l'emplacement de la chaîne de caractères multioctets à convertir.

*count*<br/>
Le nombre maximum de caractères larges à stocker dans le tampon *wcstr,* sans compter la fin nulle, ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate (en)*<br/>
Un pointeur vers un objet d’état de conversion **mbstate_t.** Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Parce que l’objet de **mbstate_t** interne n’est pas sans fil, nous vous recommandons de toujours passer votre propre paramètre *mbstate.*

## <a name="return-value"></a>Valeur de retour

Zéro si la conversion est réussie, ou un code d'erreur en cas d'échec.

|État d’erreur|Valeur de rendement et **errno**|
|---------------------|------------------------------|
|*wcstr* est un pointeur nul et *la tailleInWords* > 0|**EINVAL (EN)**|
|*mbstr* est un pointeur nul|**EINVAL (EN)**|
|La chaîne indirectement pointée vers *mbstr* contient une séquence multioctet qui n’est pas valide pour le lieu actuel.|**EILSEQ**|
|Le tampon de destination est trop petit pour contenir la chaîne convertie (à moins que *le compte* soit **_TRUNCATE**; pour plus d’informations, voir Remarques)|**ERANGE**|

Si l’une de ces conditions se produit, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

La fonction **mbsrtowcs_s** convertit une chaîne de caractères multioctets indirectement pointé par *mbstr* en caractères larges stockés dans le tampon pointé par *wcstr*, en utilisant l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère multioctet de null est rencontré.

- Un caractère multioctet non valide est rencontré.

- Le nombre de caractères larges stockés dans le tampon *wcstr* *équivaut à compter*.

Le *wcstr* de corde de destination est toujours annulé, même en cas d’erreur, à moins que *wcstr* soit un pointeur nul.

Si *le compte* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** convertit autant de la chaîne que s’insérera dans le tampon de destination, tout en laissant de la place pour un terminateur nul.

Si **mbsrtowcs_s** convertit avec succès la chaîne source, il met la taille en caractères larges de la chaîne convertie et le terminateur nul en *&#42;pReturnValue*, à condition *pReturnValue n’est* pas un pointeur nul. Cela se produit même si l’argument *wcstr* est un pointeur nul et vous permet de déterminer la taille du tampon requis. Notez que si *wcstr* est un pointeur nul, *le compte* est ignoré.

Si *le wcstr* n’est pas un pointeur nul, l’objet pointeur pointé par *mbstr* se voit attribuer un pointeur nul si la conversion s’arrête parce qu’un caractère nul de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si *mbstate* est un pointeur nul, l’objet statique interne **mbstate_t** d’état de conversion de la bibliothèque est utilisé. Parce que cet objet statique interne n’est pas sans fil, nous vous recommandons de passer votre propre valeur *mbstate.*

Si **mbsrtowcs_s** rencontre un caractère multioctet qui n’est pas valable dans le lieu actuel, il met -1 dans *&#42;pReturnValue*, définit la *wcstr* tampon de destination à une chaîne vide, définit **errno** à **EILSEQ**, et retourne **EILSEQ**.

Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbsrtowcs_s** est indéfini. **mbsrtowcs_s** est affectée par la LC_TYPE catégorie de l’endroit actuel.

> [!IMPORTANT]
> Assurez-vous que *le wcstr* et *le mbstr* ne se chevauchent pas, et ce *nombre* reflète correctement le nombre de caractères multioctets à convertir.

La fonction **mbsrtowcs_s** diffère de [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application doit utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs_s** est utilisé au lieu de **mbstowcs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et elles peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **mbsrtowcs_s** est multithread sûr si aucune fonction dans le thread actuel appelle **setlocale** tant que cette fonction est l’exécution et *l’argument mbstate n’est* pas un pointeur nul.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
