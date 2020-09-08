---
title: fabs, fabsf, fabsl
description: Informations de référence sur les API pour FABS, fabsf et fabsl ; qui calcule la valeur absolue d’une valeur à virgule flottante.
ms.date: 08/31/2020
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
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
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: a819172fc94224ff4c51c8fc342b142ffbe05ae7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554836"
---
# <a name="fabs-fabsf-fabsl"></a>fabs, fabsf, fabsl

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

*x*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **FABS** retournent la valeur absolue de l’argument *x*. Il n’y a pas d’erreur de retour.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± QNAN,IND|aucun|_DOMAIN|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **FABS** si vous incluez l' \<cmath> en-tête. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **FABS** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `fabs()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C requis|En-tête C++ requis|
|--------------|-----------------------|---------------------------|
|**FABS**, **fabsf**, **fabsl**|\<math.h>|\<cmath> ou \<math.h>|
|**FABS** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [abs](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
