---
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338886"
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
Le nombre maximum de caractères (et non d’octets) à convertir et à stocker en *wcstr.*

*mbstate (en)*<br/>
Un pointeur vers un objet d’état de conversion **mbstate_t.** Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Parce que l’objet de **mbstate_t** interne n’est pas sans fil, nous vous recommandons de toujours passer votre propre paramètre *mbstate.*

## <a name="return-value"></a>Valeur de retour

Retourne le nombre de caractères correctement convertis, non compris le caractère null de fin, le cas échéant. Retourne (size_t)(-1) en cas d’erreur, et définit **errno** à EILSEQ.

## <a name="remarks"></a>Notes

La fonction **mbsrtowcs** convertit une chaîne de caractères multioctets indirectement pointé par *mbstr*, en caractères larges stockés dans le tampon pointé vers le *wcstr*, en utilisant l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque personnage jusqu’à ce qu’un personnage multioctet nul se termine, une séquence multioctet qui ne correspond pas à un caractère valide dans le lieu actuel est rencontrée, ou jusqu’à ce que les caractères *de comptage* ont été convertis. Si **les mbsrtowcs** rencontrent le caractère nul multioctet ('0') avant ou quand *le nombre* se produit, il le convertit en un caractère nul de 16 bits mettant fin et s’arrête.

Ainsi, la large chaîne de caractère à *wcstr* n’est annulée que si **mbsrtowcs** rencontre un caractère nul multioctet pendant la conversion. Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement des **mbsrtowcs** n’est pas défini. **mbsrtowcs** est affecté par la catégorie LC_TYPE de la région actuelle.

La fonction **mbsrtowcs** diffère des [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) par sa redémarrabilité. L’état de conversion est stocké dans *mbstate* pour les appels ultérieurs vers les mêmes fonctions ou d’autres fonctions redémarrées. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application devrait utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs** est utilisé au lieu de **mbstowcs**.

Si *le wcstr* n’est pas un pointeur nul, l’objet pointeur pointé par *mbstr* se voit attribuer un pointeur nul si la conversion s’arrête parce qu’un caractère nul de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si l’argument *wcstr* est un pointeur nul, l’argument *de compte* est ignoré et **mbsrtowcs** retourne la taille requise dans les caractères larges pour la chaîne de destination. Si *mbstate* est un pointeur nul, la fonction utilise un objet d’état de conversion interne statique non-thread-safe **mbstate_t.** Si la séquence de caractère *mbstr* n’a pas une représentation de caractère multioctet correspondante, un -1 est retourné et **l’errno** est réglé à **EILSEQ**.

Si *mbstr* isa pointeur nul, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et renvoie -1.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="exceptions"></a>Exceptions

La fonction **mbsrtowcs** est multithread sûr tant que aucune fonction dans le thread actuel appelle **setlocale** tant que cette fonction est l’exécution et *l’argument mbstate n’est* pas un pointeur nul.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
