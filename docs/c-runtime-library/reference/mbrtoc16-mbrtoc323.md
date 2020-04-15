---
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340977"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Traduit le premier caractère multioctet UTF-8 dans une chaîne dans le caractère équivalent UTF-16 ou UTF-32.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
Pointeur vers le **char16_t** ou **char32_t’équivalent** du caractère multioctet UTF-8 à convertir. Si elle est nulle, la fonction ne stocke pas de valeur.

*Source*\
Pointeur vers la chaîne de caractères multioctets UTF-8 à convertir.

*max_bytes*\
Le nombre maximum d’octets à *la source* à examiner pour qu’un personnage se convertisse. Cet argument devrait être une valeur entre un et le nombre d’octets, y compris tout terminateur nul, restant à *la source*.

*État*\
Pointeur vers un objet **d’état de** conversion mbstate_t utilisé pour interpréter la chaîne multioctet UTF-8 à un ou plusieurs caractères de sortie.

## <a name="return-value"></a>Valeur retournée

Sur le succès, retourne la valeur de la première de ces conditions qui s’applique, compte tenu de la valeur actuelle *de l’État:*

|Value|Condition|
|-----------|---------------|
|0|Les *max_bytes* ou moins de caractères convertis à partir de la *source* correspondent au caractère large nul, qui est la valeur stockée si la *destination* n’est pas nulle.<br /><br /> *l’état* contient l’état de décalage initial.|
|Entre 1 et *max_bytes*, inclusivement|La valeur retournée est le nombre d’octets de *source* qui complètent un caractère multioctet valide. Le caractère large converti est stocké si *la destination* n’est pas nulle.|
|-3|Le personnage suivant large résultant d’un appel précédent à la fonction a été stocké dans la *destination* si *la destination* n’est pas nulle. Aucun octets provenant de la *source* n’est consommé par cet appel à la fonction.<br /><br /> Lorsque *la source* pointe vers un personnage multioctet UTF-8 qui nécessite plus d’un personnage large pour représenter (par exemple, une paire de substitution), puis la valeur de *l’état* est mise à jour de sorte que l’appel de fonction suivante écrit le caractère supplémentaire.|
|-2|Les *octets max_bytes* suivants représentent un caractère multioctet UTF-8 incomplet, mais potentiellement valide. Aucune valeur n’est stockée dans *la destination*. Ce résultat peut se produire si *max_bytes* est nulle.|
|-1|Une erreur d’encodage s’est produite. Les *max_bytes* ou moins d’octets suivants ne contribuent pas à un caractère complet et valide UTF-8 multioctets. Aucune valeur n’est stockée dans *la destination*.<br /><br /> **EILSEQ** est stocké dans **errno** et *l’état* de valeur de l’état de conversion n’est pas spécifié.|

## <a name="remarks"></a>Notes

La fonction **mbrtoc16** se lit jusqu’à *max_bytes* octets de la *source* pour trouver le premier caractère complet et valide UTF-8 multioctets, puis stocke le caractère équivalent UTF-16 dans *la destination*. Si le personnage nécessite plus d’un caractère de sortie UTF-16, comme une paire de substitution, alors la valeur *de l’état* est configuré pour stocker le prochain caractère UTF-16 en *destination* sur le prochain appel à **mbrtoc16**. La fonction **mbrtoc32** est identique, mais la sortie est stockée sous forme de caractère UTF-32.

Si la *source* est nulle, ces fonctions renvoient l’équivalent `""` d’un appel fait à l’aide d’arguments de **NULL** pour la *destination*, (une chaîne vide, non terminée) pour la *source*, et 1 pour *max_bytes*. Les valeurs passées de *destination* et *de max_bytes* sont ignorées.

Si la *source* n’est pas nulle, la fonction commence au début de la chaîne et inspecte *jusqu’à max_bytes* octets pour déterminer le nombre d’octets nécessaires pour compléter le prochain caractère multioctet UTF-8, y compris toutes les séquences de changement. Si les octets examinés contiennent un caractère multioctet UTF-8 valide et complet, la fonction convertit le personnage en caractère ou en caractères de large 16 ou 32 bits équivalents. Si la *destination* n’est pas nulle, la fonction stocke le premier (et peut-être seulement) le caractère de résultat dans la destination. Si des caractères de sortie supplémentaires sont nécessaires, une valeur est définie en *état,* de sorte que les appels ultérieurs à la sortie de la fonction les caractères supplémentaires et retourner la valeur -3. Si plus aucun caractère de sortie n’est requis, *l’état* est réglé à l’état de décalage initial.

Pour convertir les caractères multioctets non UTF-8 en caractères UTF-16 LE, utilisez les fonctions [mbrtowc,](mbrtowc.md) [mbtowc ou _mbtowc_l.](mbtowc-mbtowc-l.md)

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../data-conversion.md)\
[Local](../locale.md)\
[Interprétation des séquences multioctets-caractères](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc (en)](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
