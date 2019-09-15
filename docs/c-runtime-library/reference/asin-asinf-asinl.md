---
title: asin, asinf, asinl
ms.date: 04/05/2018
api_name:
- asinf
- asinl
- asin
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
ms.openlocfilehash: 1e70c9b2187b97d3dea589c1757081da8bf2bd10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943647"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Calcule l’arc sinus.

## <a name="syntax"></a>Syntaxe

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur dont l’arc sinus doit être calculé.

## <a name="return-value"></a>Valeur de retour

La fonction **ASIN** retourne l’arc sinus (fonction sinus inverse) de *x* dans la plage-π/2 à π/2 radians.

Par défaut, si *x* est inférieur à-1 ou supérieur à 1, **ASIN** retourne un indéfini.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NON VALIDE**|**_DOMAIN**|
|± **QNAN**, **IND**|none|**_DOMAIN**|
|&#124;x&#124;>1|**NON VALIDE**|**_DOMAIN**|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **ASIN** avec des valeurs **float** et **long** **double** . Dans un programme C, **ASIN** prend toujours et retourne un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**asin**, **asinf**, **asinl**|\<math.h>|\<cmath> ou \<math.h>|

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
