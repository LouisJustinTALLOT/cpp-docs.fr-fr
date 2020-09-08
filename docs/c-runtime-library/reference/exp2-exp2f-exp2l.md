---
title: exp2, exp2f, exp2l
description: Référence d’API pour EXP2 (), exp2f, () et exp2l () qui calcule 2 élevé à la valeur spécifiée.
ms.date: 9/1/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 518525a38ef575583fde3b7732561f2fa553dd18
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556617"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Calcule 2 élevé à la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
#define exp2(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur de l’exposant.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne l’exposant de base 2 de *x*, c’est-à-dire 2<sup>x</sup>. Dans le cas contraire, elle retourne l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = ± 0|1|
|*x* =-infini|+0|
|*x* = infini|+INFINITY|
|*x* = Nan|NaN|
|Erreur de plage avec dépassement|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec soupassement|Résultat correct, après arrondi|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **EXP2** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **EXP2** accepte et retourne toujours un **`double`** , sauf si vous utilisez la macro dans <tgmath. h>.

Si vous utilisez la \<tgmath.h> `exp2()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**EXP2**, **expf2**, **expl2**|\<math.h>|\<cmath>|
|**EXP2** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
