---
title: asin, asinf, asinl
description: Informations de référence sur les API pour Asin, ASInf, et asinl ; qui calcule l’arc sinus d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- asinf
- asinl
- asin
- _o_asin
- _o_asinf
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
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.openlocfilehash: 04b68e9b5933d763cecbdc06af3e34a5b7c01223
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564041"
---
# <a name="asin-asinf-asinl"></a>`asin`, `asinf`, `asinl`

Calcule l’arc sinus.

## <a name="syntax"></a>Syntaxe

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
#define asin(X) // Requires C11 or higher

float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur dont l’arc sinus doit être calculé.

## <a name="return-value"></a>Valeur renvoyée

La **`asin`** fonction retourne l’arc sinus (fonction sinus inverse) de *`x`* dans la plage-π/2 à π/2 radians.

Par défaut, si *`x`* est inférieur à-1 ou supérieur à 1, **`asin`** retourne un indéfini.

|Entrée|Exception SEH|exception Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**`INVALID`**|**`_DOMAIN`**|
|± **`QNAN`**, **`IND`**|aucun|**`_DOMAIN`**|
|&#124;x&#124;>1|**`INVALID`**|**`_DOMAIN`**|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`asin`** avec **`float`** les **`long double`** valeurs et. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`asin`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `asin()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**`asin`**, **`asinf`**, **`asinl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`asin()`** macrovirus | `<tgmath.h>` ||

## <a name="example"></a>Exemple

Pour plus d’informations, consultez [ `acos` , `acosf` , `acosl` ](acos-acosf-acosl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`acos`, `acosf`, `acosl`](acos-acosf-acosl.md)\
[`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)