---
title: fma, fmaf, fmal
ms.date: 04/05/2018
api_name:
- fma
- fmaf
- fmal
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
ms.openlocfilehash: 4ddc4061e5a24ee3b5176aedc569d134d85e0002
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957107"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Multiplie deux valeurs, ajoute une troisième valeur, puis arrondit le résultat, sans perdre de précision en raison d’un arrondi intermédiaire.

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
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur à multiplier.

*y*<br/>
Seconde valeur à multiplier.

*z*<br/>
Valeur à ajouter.

## <a name="return-value"></a>Valeur de retour

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

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **FMA** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **FMA** accepte et retourne toujours un **double**.

Cette fonction calcule la valeur avec une précision infinie, puis arrondit le résultat final.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
