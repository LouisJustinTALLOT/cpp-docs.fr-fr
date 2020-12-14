---
description: 'En savoir plus sur : mbsrtowcs'
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 83979058e33ffc3874f26cb8ef70f888195e6644
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240180"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Convertit une chaîne de caractères multioctets dans les paramètres régionaux actuels en une chaîne de caractères larges correspondante, avec la capacité de redémarrer au milieu d'un caractère multioctet. Une version plus sécurisée de cette fonction est disponible ; consultez [mbsrtowcs_s](mbsrtowcs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*wcstr*<br/>
Adresse où stocker la chaîne de caractères larges convertie.

*mbstr*<br/>
Pointeur indirect vers l'emplacement de la chaîne de caractères multioctets à convertir.

*count*<br/>
Nombre maximal de caractères (et non pas d’octets) à convertir et à stocker dans *wcstr*.

*mbstate*<br/>
Pointeur vers un objet d’état de conversion **mbstate_t** . Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Étant donné que l’objet **mbstate_t** interne n’est pas thread-safe, nous vous recommandons de toujours passer votre propre paramètre *mbstate* .

## <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de caractères correctement convertis, non compris le caractère null de fin, le cas échéant. Retourne (size_t) (-1) si une erreur s’est produite et définit **errno** sur EILSEQ.

## <a name="remarks"></a>Notes

La fonction **mbsrtowcs** convertit une chaîne de caractères multioctets indirectement pointée par *mbstr*, en caractères larges stockés dans la mémoire tampon pointée par *wcstr*, en utilisant l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu’à ce qu’un caractère multioctet null de fin soit rencontré, une séquence multioctet qui ne correspond pas à un caractère valide dans les paramètres régionaux en cours est rencontrée, ou jusqu’à ce que les caractères *Count* aient été convertis. Si **mbsrtowcs** rencontre le caractère null multioctet (' \ 0 ') avant ou quand *Count* se produit, il le convertit en un caractère null de fin 16 bits et s’arrête.

Ainsi, la chaîne de caractères larges sur *wcstr* est terminée par un caractère NULL uniquement si **mbsrtowcs** rencontre un caractère null multioctet pendant la conversion. Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbsrtowcs** n’est pas défini. **mbsrtowcs** est affecté par la catégorie LC_TYPE des paramètres régionaux actuels.

La fonction **mbsrtowcs** diffère de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) par son redémarrage. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou à d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs** est utilisé à la place de **mbstowcs**.

Si *wcstr* n’est pas un pointeur null, l’objet pointeur désigné par *mbstr* reçoit un pointeur null si la conversion s’est arrêtée, car un caractère null de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si l’argument *wcstr* est un pointeur null, l’argument *Count* est ignoré et **mbsrtowcs** retourne la taille requise en caractères larges pour la chaîne de destination. Si *mbstate* est un pointeur null, la fonction utilise un objet d’état de conversion **mbstate_t** statique non thread-safe. Si la séquence de caractères *mbstr* n’a pas de représentation de caractères multioctets correspondante, la valeur-1 est retournée et la valeur de **errno** est **EILSEQ**.

Si *mbstr* ISA null pointeur, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne-1.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **mbsrtowcs** est multithread Safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** tant que cette fonction est en cours d’exécution et que l’argument *mbstate* n’est pas un pointeur null.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
