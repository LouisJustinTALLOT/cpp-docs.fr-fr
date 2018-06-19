---
title: fdim, fdimf, fdiml | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdcad02c94717715fdda1b3a9d2e820fc16d0bf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397504"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Détermine la différence positive entre les première et deuxième valeurs.

## <a name="syntax"></a>Syntaxe

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur.

*y*<br/>
Seconde valeur.

## <a name="return-value"></a>Valeur de retour

Retourne la différence positive entre *x* et *y*:

|Valeur de retour|Scénario|
|------------------|--------------|
|x-y|Si x > y|
|0|Si x <= y|

Sinon, peut retourner l’une des erreurs suivantes :

|Problème|Retourner|
|-----------|------------|
|Erreur de plage avec dépassement|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec soupassement|valeur correcte (après arrondi)|
|*x* ou *y* est NaN|NaN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **fdim** qui acceptent et retournent **float** et **long** **double** types. Dans un programme C, **fdim** accepte et retourne toujours un **double**.

À l’exception de la gestion de la valeur NaN, cette fonction est équivalente à `fmax(x - y, 0)`.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fdim**, **fdimf**, **fdiml**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
