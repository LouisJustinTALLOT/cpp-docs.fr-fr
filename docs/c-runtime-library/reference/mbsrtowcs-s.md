---
title: mbsrtowcs_s
ms.date: 11/04/2016
apiname:
- mbsrtowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: a935b5181078f3b08ba5f2f89c581ed8cce8ded5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588824"
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

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
La taille de *wcstr* en mots (caractères larges).

*mbstr*<br/>
Pointeur indirect vers l'emplacement de la chaîne de caractères multioctets à convertir.

*count*<br/>
Le nombre maximal de caractères larges à stocker dans le *wcstr* mémoire tampon, non compris le caractère null de fin, ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet d’état de conversion. Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Étant donné que le texte interne **mbstate_t** objet n’est pas thread-safe, nous vous recommandons de toujours passer votre propre *mbstate* paramètre.

## <a name="return-value"></a>Valeur de retour

Zéro si la conversion est réussie, ou un code d'erreur en cas d'échec.

|Condition d'erreur|Valeur de retour et **errno**|
|---------------------|------------------------------|
|*wcstr* est un pointeur null et *sizeInWords* > 0|**EINVAL**|
|*mbstr* est un pointeur null|**EINVAL**|
|La chaîne indirectement pointée par *mbstr* contient une séquence multioctet qui n’est pas valide pour les paramètres régionaux actuels.|**EILSEQ**|
|La mémoire tampon de destination est trop petite pour contenir la chaîne convertie (à moins que *nombre* est **_TRUNCATE**; pour plus d’informations, consultez la section Notes)|**ERANGE**|

Si l’une de ces conditions se produit, l’exception de paramètre non valide est appelée, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne un code d’erreur et définit **errno** comme indiqué dans le tableau.

## <a name="remarks"></a>Notes

Le **mbsrtowcs_s** fonction convertit une chaîne de caractères multioctets indirectement pointée par *mbstr* en caractères larges stockés dans la mémoire tampon vers laquelle pointée *wcstr*, par à l’aide de l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu'une des conditions suivantes soit remplie :

- Un caractère multioctet de null est rencontré.

- Un caractère multioctet non valide est rencontré.

- Le nombre de caractères larges stockés dans le *wcstr* mettre en mémoire tampon est égale à *nombre*.

La chaîne de destination *wcstr* est toujours terminée par null, même en cas d’une erreur, sauf si *wcstr* est un pointeur null.

Si *nombre* est la valeur spéciale [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** convertit autant de caractères de la chaîne en tenir dans la mémoire tampon de destination, tout en laissant la place pour une valeur null marque de fin.

Si **mbsrtowcs_s** convertit correctement la chaîne source, elle place la taille en caractères larges de la chaîne convertie et la marque de fin null dans  *&#42;pReturnValue*, fourni  *pReturnValue* n’est pas un pointeur null. Cela se produit même si le *wcstr* argument est un pointeur null et vous permet de déterminer la taille de mémoire tampon requise. Notez que si *wcstr* est un pointeur null, *nombre* est ignoré.

Si *wcstr* n’est pas un pointeur null, l’objet de pointeur pointé par *mbstr* reçoit un pointeur null si la conversion a été arrêtée, car un caractère null de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si *mbstate* est un pointeur null, la bibliothèque interne **mbstate_t** objet d’état de conversion statique est utilisé. Étant donné que cet objet statique interne n’est pas thread-safe, nous vous recommandons de passer votre propre *mbstate* valeur.

Si **mbsrtowcs_s** rencontre un caractère multioctet qui n’est pas valid dans les paramètres régionaux actuels, il place -1  *&#42;pReturnValue*, définit la mémoire tampon de destination *wcstr* une chaîne vide, définit **errno** à **EILSEQ**et retourne **EILSEQ**.

Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbsrtowcs_s** n’est pas défini. **mbsrtowcs_s** est affectée par la catégorie LC_TYPE des paramètres régionaux actuels.

> [!IMPORTANT]
> Vérifiez que *wcstr* et *mbstr* ne se chevauchent pas et qui *nombre* reflète fidèlement le nombre de caractères multioctets à convertir.

Le **mbsrtowcs_s** diffère de la fonction [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables. Par exemple, une application doit utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs_s** est utilisé au lieu de **mbstowcs_s**.

En C++, l’utilisation de cette fonction est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument de taille) et elles peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalents plus récents et sécurisés. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **mbsrtowcs_s** fonction est multithread-safe si aucune fonction dans le thread actif n’appelle **setlocale** tant que l’exécution de cette fonction et le *mbstate* argument est pas un pointeur null.

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
