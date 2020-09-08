---
title: fdim, fdimf, fdiml
description: Informations de référence sur les API pour FDIM, fdimf et fdiml ; qui détermine la différence positive entre deux valeurs.
ms.date: 9/1/2020
api_name:
- fdim
- fdimf
- fdiml
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 406fc5cfe543aa0865760df9ff780c62e78510fc
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554784"
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

#define fdim(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Première valeur.

*y*\
Seconde valeur.

## <a name="return-value"></a>Valeur renvoyée

Retourne la différence positive entre *x* et *y*:

|Valeur renvoyée|Scénario|
|------------------|--------------|
|x-y|Si x > y|
|0|Si x <= y|

Sinon, peut retourner l’une des erreurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|Erreur de plage avec dépassement|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec soupassement|valeur correcte (après arrondi)|
|*x* ou *y* est NaN|NaN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **FDIM** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **FDIM** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `fdim()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

À l’exception de la gestion NaN, cette fonction est équivalente à `fmax(x - y, 0)` .

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**FDIM**, **fdimf**, **fdiml**|\<math.h>|\<cmath>|
|**FDIM** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
