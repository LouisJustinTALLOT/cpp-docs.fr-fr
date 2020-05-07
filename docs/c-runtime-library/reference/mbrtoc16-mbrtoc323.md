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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0e3d5ceffa5adc9e9f6ba96cccb46a3fbcfca69a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919565"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Traduit le premier caractère multioctet UTF-8 dans une chaîne en un caractère équivalent UTF-16 ou UTF-32.

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

*destination*\
Pointeur vers le **char16_t** ou **char32_t** équivalent du caractère multioctet UTF-8 à convertir. Si la valeur est null, la fonction ne stocke pas de valeur.

*code*\
Pointeur vers la chaîne de caractères multioctets UTF-8 à convertir.

*max_bytes*\
Nombre maximal d’octets dans la *source* à examiner pour un caractère à convertir. Cet argument doit être une valeur comprise entre 1 et le nombre d’octets, y compris toute marque de fin null, restant dans la *source*.

*Département*\
Pointeur vers un objet d’état de conversion **mbstate_t** utilisé pour interpréter la chaîne multioctets UTF-8 à un ou plusieurs caractères de sortie.

## <a name="return-value"></a>Valeur retournée

En cas de réussite, retourne la valeur de la première des conditions qui s’applique, étant donné la valeur d' *État* actuelle :

|Value|Condition|
|-----------|---------------|
|0|Le *max_bytes* suivant ou un nombre de caractères inférieur converti à partir de la *source* correspond au caractère élargi null, qui est la valeur stockée si *destination* n’est pas null.<br /><br /> l' *État* contient l’état de décalage initial.|
|Entre 1 et *max_bytes*inclus|La valeur retournée est le nombre d’octets de la *source* qui terminent un caractère multioctet valide. Le caractère élargi converti est stocké si la *destination* n’est pas null.|
|-3|Le caractère élargi suivant résultant d’un appel précédent à la fonction a été stocké dans la *destination* si la *destination* n’est pas null. Aucun octet de la *source* n’est consommé par cet appel à la fonction.<br /><br /> Lorsque la *source* pointe vers un caractère multioctet UTF-8 qui requiert plusieurs caractères larges à représenter (par exemple, une paire de substitution), la valeur d' *État* est mise à jour afin que l’appel de fonction suivant écrive le caractère supplémentaire.|
|-2|Les octets *max_bytes* suivants représentent un caractère multioctet UTF-8 incomplet, mais potentiellement valide. Aucune valeur n’est stockée dans la *destination*. Ce résultat peut se produire si *max_bytes* est égal à zéro.|
|-1|Une erreur d’encodage s’est produite. Le *max_bytes* suivant ou moins d’octets ne contribuent pas à un caractère multioctet UTF-8 complet et valide. Aucune valeur n’est stockée dans la *destination*.<br /><br /> **EILSEQ** est stocké dans **errno** et l' *État* de la valeur de l’état de conversion n’est pas spécifié.|

## <a name="remarks"></a>Notes 

La fonction **mbrtoc16** lit jusqu’à *max_bytes* octets à partir de la *source* pour rechercher le premier caractère multioctet UTF-8 valide complet, puis stocke le caractère UTF-16 équivalent dans la *destination*. Si le caractère requiert plus d’un caractère de sortie UTF-16, par exemple une paire de substitution, la valeur d' *État* est définie pour stocker le prochain caractère UTF-16 dans la *destination* lors du prochain appel à **mbrtoc16**. La fonction **mbrtoc32** est identique, mais la sortie est stockée sous la forme d’un caractère UTF-32.

Si *source* a la valeur null, ces fonctions retournent l’équivalent d’un appel effectué à *destination*l’aide `""` des arguments **null** pour la destination, (une chaîne vide se terminant par null) pour la *source*, et 1 pour *max_bytes*. Les valeurs passées de *destination* et *max_bytes* sont ignorées.

Si *source* n’est pas null, la fonction commence au début de la chaîne et inspecte jusqu’à *max_bytes* octets pour déterminer le nombre d’octets requis pour terminer le caractère multioctet UTF-8 suivant, y compris les séquences de décalage. Si les octets examinés contiennent un caractère multioctet UTF-8 valide et complet, la fonction convertit le caractère en caractères larges 16 bits ou 32 bits équivalents. Si *destination* n’est pas null, la fonction stocke le premier (et éventuellement) caractère de résultat dans la destination. Si des caractères de sortie supplémentaires sont nécessaires, une valeur est définie dans *État*, de sorte que les appels suivants à la fonction génèrent les caractères supplémentaires et retournent la valeur-3. Si aucun autre caractère de sortie n’est requis, *State* est défini sur l’état de décalage initial.

Pour convertir des caractères multioctets non UTF-8 en caractères UTF-16, utilisez les fonctions [mbrtowc](mbrtowc.md), [mbtowc ou _mbtowc_l](mbtowc-mbtowc-l.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../data-conversion.md)\
[Paramètres régionaux](../locale.md)\
[Interprétation des séquences de caractères multioctets](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
