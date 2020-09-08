---
title: fma, fmaf, fmal
description: Informations de référence sur les API pour FMA, fmaf et Fmal ; qui multiplie deux valeurs, ajoute une troisième valeur, puis arrondit le résultat, sans perdre de précision en raison de l’arrondi intermédiaire.
ms.date: 9/1/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: e9ae92c28f24b6281d73450c7cabaad775a84d42
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556695"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Multiplie deux valeurs, ajoute une troisième valeur, puis arrondit le résultat, sans perdre de précision en raison de l’arrondi intermédiaire.

## <a name="syntax"></a>Syntaxe

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);

#define fma(X, Y, Z) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Première valeur à multiplier.

*y*\
Seconde valeur à multiplier.

*Lettre*\
Valeur à ajouter.

## <a name="return-value"></a>Valeur renvoyée

Retourne `(x * y) + z`. La valeur de retour est ensuite arrondie à l’aide du format d’arrondi actuel.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = Infinity, *y* = 0 ou<br /><br /> *x* = 0, *y* = infini|NaN|
|*x* ou *y* = exact ± infini, *z* = infini avec le signe opposé|NaN|
|*x* ou *y* = Nan|NaN|
|Not (*x* = 0, *y*= indéfini) et *z* = Nan<br /><br /> Not (*x*= indéterminé, *y*= 0) et *z* = Nan|NaN|
|Erreur de plage avec dépassement|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|
|Erreur de plage avec soupassement|valeur correcte, après arrondi.|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **FMA** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **FMA** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `fma()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Cette fonction calcule la valeur avec une précision infinie, puis arrondit le résultat final.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf**, **Fmal**|\<math.h>|\<cmath>|
|**FMA** , macro | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
