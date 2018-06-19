---
title: tgamma, tgammaf, tgammal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- tgamma
- tgammaf
- tgammal
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs:
- C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7861b297646f4a704134e0d874fad8c924a7ebc8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409873"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Détermine la fonction gamma de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);

```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur dont le gamma doit être trouvé.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur gamma de *x*.

Une erreur de plage peut se produire si la grandeur de *x* est trop grande ou trop petite pour le type de données. Une erreur de domaine ou d’une erreur de plage peut se produire si *x* < = 0.

|Problème|Retourner|
|-----------|------------|
|x = ±0|±INFINITY|
|x = entier négatif|NaN|
|x = - INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Erreur de domaine|NaN|
|erreur de pôle|±HUGE_VAL, ±HUGE_VALF ou ±HUGE_VALL|
|erreur de plage avec dépassement de capacité positif|±HUGE_VAL, ±HUGE_VALF ou ±HUGE_VALL|
|erreur de plage avec dépassement de capacité négatif|valeur correcte après arrondi|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **tgamma** qui acceptent et retournent **float** et **long** **double** types. Dans un programme C, **tgamma** accepte et retourne toujours un **double**.

Si x est un nombre naturel, cette fonction retourne la factorielle de (x-1).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
