---
description: 'En savoir plus sur : fetestexcept'
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: 8a62ae33f2965916bd16e2e854555bf22d87a0cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289385"
---
# <a name="fetestexcept"></a>fetestexcept

Détermine les indicateurs d’état d’exception de virgule flottante spécifiés qui sont définis.

## <a name="syntax"></a>Syntaxe

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>Paramètres

*sauf*<br/>
Opération OR au niveau du bit des indicateurs d’état à virgule flottante à tester.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne un masque de bits qui contient une opération OR au niveau du bit des macros d’exception de virgule flottante qui correspondent aux indicateurs d’état d’exception définis. Retourne 0 si aucune des exceptions n’est définie.

## <a name="remarks"></a>Notes

La fonction fetestexcept permet de déterminer les exceptions levées par une opération à virgule flottante. Utilisez le paramètre *EXCEPTS* pour spécifier les indicateurs d’état d’exception à tester. La fonction **fetestexcept** utilise les macros d’exception définies dans \<fenv.h> dans, à l' *exception* de et la valeur de retour :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALL_EXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

L’argument *EXCEPTS* spécifié peut être 0, l’une des macros d’exception de virgule flottante prises en charge ou l’opération or au niveau du bit d’au moins deux macros. L’effet de toute autre valeur d’argument *except* n’est pas défini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
