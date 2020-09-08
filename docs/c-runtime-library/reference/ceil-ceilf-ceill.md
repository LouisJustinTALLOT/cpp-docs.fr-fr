---
title: ceil, ceilf, ceill
description: Référence d’API pour calcuating le plafond d’une valeur avec ceil ().
ms.date: 9/1/2020
api_name:
- ceilf
- ceil
- ceill
- _o_ceil
- _o_ceilf
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ceil
- ceilf
- ceill
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
ms.openlocfilehash: 3079f52c79d6d888923025357bb21adc782aa5cd
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555241"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Calcule le plafond d’une valeur.

## <a name="syntax"></a>Syntaxe

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
#define ceil(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **ceil** retournent une valeur à virgule flottante qui représente le plus petit entier supérieur ou égal à *x*. Il n’y a pas d’erreur de retour.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|

**ceil** a une implémentation qui utilise SSE2 (streaming SIMD Extensions 2). Pour plus d’informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ceil** qui acceptent **`float`** des **`long double`** types ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **ceil** accepte et retourne toujours un **`double`** .

Si vous utilisez la macro <tgmath. h> `ceil()` , le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ceil**, **ceilf,**, **ceill**|\<math.h>|
|**ceil** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [floor](floor-floorf-floorl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
