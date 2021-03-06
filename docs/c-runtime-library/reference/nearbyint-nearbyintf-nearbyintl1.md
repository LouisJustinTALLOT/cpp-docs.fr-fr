---
title: nearbyint, nearbyintf, nearbyintl
description: Informations de référence sur les API pour nearbyint, nearbyintf et nearbyintl ; qui arrondit la valeur à virgule flottante spécifiée à un entier et retourne cette valeur dans un format à virgule flottante.
ms.date: 9/1/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 9717559518032c6f1f2126c7ded7cb90603bce64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556383"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Arrondit la valeur à virgule flottante spécifiée en un entier et retourne cette valeur dans un format à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
#define nearbyint( X ) // Requires C11 or higher

float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à arrondir.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne *x*, arrondi à l’entier le plus proche, en utilisant le format d’arrondi actuel comme indiqué par [fegetround](fegetround-fesetround2.md). Sinon, la fonction peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = ± infini|± INFINI, non modifié|
|*x* = ± 0|± 0, non modifié|
|*x* = Nan|NaN|

Les erreurs ne sont pas signalées par [_matherr](matherr.md); plus précisément, cette fonction ne signale pas d’exception **FE_INEXACT** .

## <a name="remarks"></a>Notes

La principale différence entre cette fonction et l' [Imprimer](rint-rintf-rintl.md) est que cette fonction ne génère pas l’exception à virgule flottante inexacte.

Étant donné que les valeurs à virgule flottante maximales sont des entiers exacts, cette fonction ne provoque jamais de dépassement par elle-même. Cependant, la sortie peut dépasser la valeur de retour, selon la version de la fonction que vous utilisez.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **nearbyint** qui acceptent et retournent des **`float`** **`long double`** paramètres ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **nearbyint** prend toujours deux valeurs doubles et retourne une valeur double.

Si vous utilisez la \<tgmath.h> `nearbyint()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> ou \<math.h>|
|**nearbyint** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[Prise en charge des fonctions mathématiques et à virgule flottante](../floating-point-support.md)<br/>
