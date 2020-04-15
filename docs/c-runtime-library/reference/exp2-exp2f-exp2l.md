---
title: exp2, exp2f, exp2l
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a5df1a216b4565f013a4c42b4ef4369b5b7f9b04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347581"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Calculs 2 portés à la valeur spécifiée.

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
```

### <a name="parameters"></a>Paramètres

*X*<br/>
Valeur de l’exposant.

## <a name="return-value"></a>Valeur de retour

En cas de succès, retourne l’exposant de base-2 de *x*, c’est-à-dire 2<sup>x</sup>. Sinon, il renvoie l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* 0 euros|1|
|*x* -INFINITY|+0|
|*x* ' 'INFINITY'|+INFINITY|
|*x* NaN|NaN|
|Erreur de plage avec dépassement|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec soupassement|Résultat correct, après l’arrondissement|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Étant donné que le CMD permet la surcharge, vous pouvez appeler des surcharges **d’exp2** qui prennent et retournent **flotteur** et **de longs types doubles.** Dans un programme C, **exp2** prend toujours et retourne un **double**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**exp**, **expf**, **expl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
