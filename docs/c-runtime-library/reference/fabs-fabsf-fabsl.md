---
title: fabs, fabsf, fabsl
description: Informations de référence sur les API pour FABS, fabsf et fabsl ; qui calcule la valeur absolue d’une valeur à virgule flottante.
ms.date: 1/15/2021
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
- _o_fabsf
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.openlocfilehash: 453965b846dff9affb3fa6dce99ea8b6189a5d6c
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563924"
---
# <a name="fabs-fabsf-fabsl"></a>`fabs`, `fabsf`, `fabsl`

Calcule la valeur absolue de l’argument à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);

#define fabs(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les **`fabs`** fonctions retournent la valeur absolue de l’argument *x*. Il n’y a pas d’erreur de retour.

|Entrée|Exception SEH|`Matherr` titre|
|-----------|-------------------|-----------------------|
|± `QNAN`,`IND`|aucun|`_DOMAIN`|

## <a name="remarks"></a>Remarques

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`fabs`** si vous incluez l' `<cmath>` en-tête. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`fabs`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `fabs()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C requis|En-tête C++ requis|
|--------------|-----------------------|---------------------------|
|**`fabs`**, **`fabsf`**, **`fabsl`**|`<math.h>`|`<cmath>` ou `<math.h>`|
|**`fabs`** macrovirus | `<tgmath.h>` ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple pour [`abs`](abs-labs-llabs-abs64.md) .

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`abs, labs, llabs, _abs64`](abs-labs-llabs-abs64.md)\
[`_cabs`](cabs.md)
