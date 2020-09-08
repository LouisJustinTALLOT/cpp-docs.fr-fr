---
title: asin, asinf, asinl
description: Informations de référence sur les API pour Asin, ASInf, et asinl ; qui calcule l’arc sinus d’une valeur à virgule flottante.
ms.date: 08/31/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
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
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 7167debcfb605ab05720d9441943439ea9982324
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556656"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

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

*x*\
Valeur dont l’arc sinus doit être calculé.

## <a name="return-value"></a>Valeur renvoyée

La fonction **ASIN** retourne l’arc sinus (fonction sinus inverse) de *x* dans la plage-π/2 à π/2 radians.

Par défaut, si *x* est inférieur à-1 ou supérieur à 1, **ASIN** retourne un indéfini.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**Non valide**|**_DOMAIN**|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|
|&#124;x&#124;>1|**Non valide**|**_DOMAIN**|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ASIN** avec **`float`** des **`long double`** valeurs et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **ASIN** prend toujours et retourne un **`double`** .

Si vous utilisez la \<tgmath.h> `asin()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**ASIN**, **ASInf,**, **asinl**|\<math.h>|\<cmath> ou \<math.h>|
|**ASIN () (macro)** | \<tgmath.h> ||

## <a name="example"></a>Exemple

Pour plus d’informations, consultez [acos, acosf, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
