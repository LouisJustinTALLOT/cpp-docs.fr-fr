---
description: 'En savoir plus sur : feclearexcept'
title: feclearexcept1
ms.date: 04/05/2018
api_name:
- feclearexcept
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
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 09eb34ddb781a40418152ec8cc6893074c58a617
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322587"
---
# <a name="feclearexcept"></a>feclearexcept

Tente d’effacer les indicateurs d’exception de virgule flottante spécifiés par l’argument.

## <a name="syntax"></a>Syntaxe

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Paramètres

*sauf*<br/>
Indicateurs d’état d’exception à effacer.

## <a name="return-value"></a>Valeur renvoyée

Retourne zéro si *except* est égal à zéro, ou si toutes les exceptions spécifiées ont été correctement effacées. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

La fonction **feclearexcept** tente d’effacer les indicateurs d’état d’exception de virgule flottante spécifiés par *sauf*. La fonction prend en charge les macros d’exception suivantes, définies dans fenv.h :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALL_EXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

L’argument *EXCEPTS* peut être égal à zéro ou au niveau du bit ou d’une ou plusieurs des macros d’exception prises en charge. Le résultat de toute autre valeur d’argument est indéfini.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
