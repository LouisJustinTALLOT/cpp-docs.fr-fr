---
title: fmin, fminf, fminl
description: Informations de référence sur les API pour fmin,, fminf, et fminl ; qui détermine la plus petite de deux valeurs.
ms.date: 9/1/2020
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: 6a070835d809c6adcb5b7bfd57b5373886b348ca
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556708"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Détermine la plus petite de deux valeurs spécifiées.

## <a name="syntax"></a>Syntaxe

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Première valeur à comparer.

*y*\
Deuxième valeur à comparer.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne la valeur la plus petite de *x* ou *y*.

|Entrée|Résultats|
|-----------|------------|
|*x* est NaN|*y*|
|*y* est NaN|*x*|
|*x* et *y* sont des Nan|NaN|

La fonction ne provoque pas l’appel de [_matherr](matherr.md) , provoque des exceptions à virgule flottante ou modifie la valeur de **errno**.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **fmin,** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **fmin,** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `fmin()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**fmin,**, **fminf,**, **fminl**|Secteur \<math.h><br />C++ : \<math.h> ou \<cmath>|
|**fmin,** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
