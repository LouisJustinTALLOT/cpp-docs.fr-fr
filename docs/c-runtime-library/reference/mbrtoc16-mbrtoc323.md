---
title: mbrtoc16, mbrtoc323 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs:
- C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a12e90f9a4bc0cc27df421c27d77a1b9b69334b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405300"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Traduit le premier caractère multioctet dans une chaîne étroite en caractère équivalent UTF-16 ou UTF-32.

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

*Destination*<br/>
Pointeur vers le **char16_t** ou **char32_t** équivalent du caractère multioctet à convertir. Si vous spécifiez la valeur null, la fonction ne stocke pas de valeur.

*Source*<br/>
Pointeur vers la chaîne de caractères multioctets à convertir.

*max_bytes*<br/>
Le nombre maximal d’octets dans *source* à examiner pour un caractère à convertir. Cela doit être une valeur comprise entre 1 et le nombre d’octets, y compris toute marque de fin null, restant dans *source*.

*state*<br/>
Pointeur vers un **mbstate_t** objet d’état de conversion utilisé pour interpréter la chaîne multioctets à un ou plusieurs caractères de sortie.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur de la première de ces conditions s’applique, étant donné l’actuel *état* valeur :

|Value|Condition|
|-----------|---------------|
|0|La prochaine *max_bytes* ou moins de caractères converties à partir de *source* correspond au caractère large null, qui est la valeur stockée si *destination* n’est pas null.<br /><br /> *état* contient l’état du décalage initial.|
|Compris entre 1 et *max_bytes*(inclus)|La valeur retournée est le nombre d’octets de *source* qui terminent un caractère multioctet valide. Les caractères larges convertis sont stockés si *destination* n’est pas null.|
|-3|Le caractère large suivant résultant d’un appel précédent à la fonction a été stocké dans *destination* si *destination* n’est pas null. Aucun octet à partir de *source* sont consommés par cet appel à la fonction.<br /><br /> Lorsque *source* pointe vers un caractère multioctet qui nécessite plus d’un caractère large à représenter (par exemple, une paire de substitution), puis le *état* valeur est mise à jour afin que l’appel de fonction suivant écrit  le caractère supplémentaire.|
|-2|La prochaine *max_bytes* octets représentent un incomplet, mais potentiellement valide caractère multioctet. Aucune valeur n’est stockée dans *destination*. Ce résultat peut se produire si *max_bytes* est égal à zéro.|
|-1|Une erreur d’encodage s’est produite. La prochaine *max_bytes* ou un nombre d’octets ne contribue pas à un caractère multioctet complet et valide. Aucune valeur n’est stockée dans *destination*.<br /><br /> **EILSEQ** est stocké dans **errno** et l’état de conversion *état* n’est pas spécifié.|

## <a name="remarks"></a>Notes

Le **mbrtoc16** fonction lit jusqu'à *max_bytes* octets à partir de *source* pour rechercher le premier caractère multioctet complet et valide, puis stocke l’équivalent UTF-16 caractère de *destination*. Les octets sources sont interprétés en fonction des paramètres régionaux multioctets du thread actif. Si le caractère multioctet nécessite plusieurs caractères de sortie UTF-16, par exemple une paire de substitution, puis le *état* a la valeur à stocker le caractère UTF-16 suivant dans *destination* lors du prochain appel à **mbrtoc16**. Le **mbrtoc32** fonction est identique, mais le résultat est stocké comme un caractère UTF-32.

Si *source* est null, ces fonctions retournent l’équivalent d’un appel effectué à l’aide des arguments de **NULL** pour *destination*, **» «** pour *source*et 1 pour *max_bytes*. Les valeurs passées de *destination* et *max_bytes* sont ignorés.

Si *source* est non null, la fonction commence au début de la chaîne et elle inspecte jusqu'à *max_bytes* octets pour déterminer le nombre d’octets requis pour terminer le caractère multioctet suivant, y compris les séquences de décalage. Si les octets examinés contiennent un caractère multioctet valide et complet, la fonction convertit le caractère en caractères larges 16 bits ou 32 bits équivalents. Si *destination* n’est ne pas null, la fonction stocke le résultat du premier (et éventuellement unique) caractère dans la destination. Si les caractères de sortie supplémentaires sont requises, une valeur est définie *état*, de sorte que les appels suivants à la fonction génèrent les caractères supplémentaires et retournent la valeur de -3. Si aucun autre caractère de sortie n’est requis, puis *état* est définie sur l’état du décalage initial.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
