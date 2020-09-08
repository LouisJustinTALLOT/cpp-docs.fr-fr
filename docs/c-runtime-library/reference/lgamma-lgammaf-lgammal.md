---
title: lgamma, lgammaf, lgammal
description: Informations de référence sur les API pour lgamma, lgammaf et lgammal ; qui détermine le logarithme népérien de la valeur absolue de la fonction gamma de la valeur spécifiée.
ms.date: 9/1/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 202250f3575f61fcef1cf29a687b8fdf36e6db33
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555395"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Détermine le logarithme népérien de la valeur absolue de la fonction gamma de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
#define lgammal(X) // Requires C11 or higher

float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à calculer.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne le logarithme népérien de la valeur absolue de la fonction gamma de *x*.

|Problème|Renvoie|
|-----------|------------|
|*x* = Nan|NaN|
|*x* = ± 0|+INFINITY|
|*x*= entier négatif|+INFINITY|
|± INFINI|+INFINITY|
|Erreur de pôle|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec dépassement|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **lgamma** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **lgamma** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `lgamma()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Si x est un nombre rationnel, cette fonction retourne le logarithme de la factorielle de (x-1).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammal**|\<math.h>|\<cmath>|
|**lgamma** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
