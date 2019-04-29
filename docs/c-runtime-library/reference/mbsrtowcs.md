---
title: mbsrtowcs
ms.date: 11/04/2016
apiname:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 2bc0c8c9e2d871b6d1748c42dc02c627244dbf69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331140"
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
Le nombre maximal de caractères (non en octets) pour convertir et stocker dans *wcstr*.

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet d’état de conversion. Si cette valeur est un pointeur null, un objet d'état de conversion interne statique est utilisé. Étant donné que le texte interne **mbstate_t** objet n’est pas thread-safe, nous vous recommandons de toujours passer votre propre *mbstate* paramètre.

## <a name="return-value"></a>Valeur de retour

Retourne le nombre de caractères correctement convertis, non compris le caractère null de fin, le cas échéant. Retourne (size_t)(-1) si une erreur s’est produite et définit **errno** à EILSEQ.

## <a name="remarks"></a>Notes

Le **mbsrtowcs** fonction convertit une chaîne de caractères multioctets indirectement pointée par *mbstr*, en caractères larges stockés dans la mémoire tampon vers laquelle pointée *wcstr*, par à l’aide de l’état de conversion contenu dans *mbstate*. La conversion se poursuit pour chaque caractère jusqu'à ce qu’un caractère null multioctet caractère est rencontré, une séquence multioctet qui ne correspond pas à un caractère valide dans les paramètres régionaux actuels est rencontrée, ou jusqu'à ce que *nombre* caractères ont été convertis. Si **mbsrtowcs** rencontre le caractère null multioctet ('\0') avant ou quand *nombre* se produit, il est converti en un caractère null de fin 16 bits et s’arrête.

Par conséquent, la chaîne de caractères larges à *wcstr* est nul uniquement si **mbsrtowcs** rencontre un caractère null multioctet pendant la conversion. Si les séquences pointées par *mbstr* et *wcstr* se chevauchent, le comportement de **mbsrtowcs** n’est pas défini. **mbsrtowcs** est affectée par la catégorie LC_TYPE des paramètres régionaux actuels.

Le **mbsrtowcs** diffère de la fonction [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, une application doit utiliser **mbsrlen** au lieu de **mbslen**, si un appel ultérieur à **mbsrtowcs** est utilisé au lieu de **mbstowcs**.

Si *wcstr* n’est pas un pointeur null, l’objet de pointeur pointé par *mbstr* reçoit un pointeur null si la conversion a été arrêtée, car un caractère null de fin a été atteint. Sinon, il est affecté de l'adresse qui se trouve juste après le dernier caractère multioctet converti, le cas échéant. Ceci permet à un appel de fonction ultérieur de redémarrer la conversion où cet appel s'est arrêté.

Si le *wcstr* argument est un pointeur null, le *nombre* argument est ignoré et **mbsrtowcs** retourne la taille requise en caractères larges pour la chaîne de destination. Si *mbstate* est un pointeur null, la fonction utilise un interne statique de thread-safe **mbstate_t** objet d’état de conversion. Si la séquence de caractères *mbstr* n’a pas un multioctets correspondants représentation sous forme de caractère, une valeur -1 est retournée et le **errno** a la valeur **EILSEQ**.

Si *mbstr* un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne -1.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **mbsrtowcs** fonction est multithread-safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** tant que l’exécution de cette fonction et le *mbstate* argument n’est pas un pointeur null.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
