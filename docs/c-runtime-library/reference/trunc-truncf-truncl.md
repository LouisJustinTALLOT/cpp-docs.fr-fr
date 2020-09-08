---
title: trunc, truncf, truncl
description: Informations de référence sur l’API pour trunc, truncf,, truncl ; qui détermine l’entier le plus proche qui est inférieur ou égal à la valeur à virgule flottante spécifiée.
ms.date: 9/1/2020
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: f1f2fde95bb944aa461bb95a9ad30fac204552b9
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556630"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Détermine l’entier le plus proche dont la valeur est inférieure ou égale à la valeur à virgule flottante spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double trunc( double x );
long double truncl( long double x );
#define trunc(X) // Requires C11 or higher

long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à tronquer.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne une valeur entière de *x*, arrondie à zéro.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = ± infini|x|
|*x* = ± 0|x|
|*x* = Nan|NaN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **trunc** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **trunc** prend toujours et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `trunc()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Comme les valeurs à virgule flottante les plus grandes sont des entiers exacts, cette fonction ne provoque pas de dépassement de capacité. Cependant, vous pouvez causer le dépassement de capacité de la fonction en retournant une valeur sous dans un type entier.

Vous pouvez aussi arrondir vers le bas en convertissant de manière implicite une valeur à virgule flottante en entier ; cependant, cette opération se limite aux valeurs qui peuvent être stockées dans le type cible.

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**trunc**, **truncf,**, **truncl**|\<math.h>|\<cmath>|
|**trunc** , macro | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
