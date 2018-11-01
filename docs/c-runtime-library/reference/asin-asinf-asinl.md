---
title: asin, asinf, asinl
ms.date: 04/05/2018
apiname:
- asinf
- asinl
- asin
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 20a2ffc37ea666207b9558cb5c282c414cfd4838
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476045"
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

Le **asin** fonction retourne l’arc sinus (la fonction sinus inverse) de *x* dans la plage π/2 et π/2 radians.

Par défaut, si *x* est inférieur à -1 ou supérieur à 1, **asin** retourne un indéfini.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NON VALIDE**|**_DOMAINE**|
|+ **QNAN**, **IND**|none|**_DOMAINE**|
|&#124;x&#124;>1|**NON VALIDE**|**_DOMAINE**|

## <a name="remarks"></a>Notes

Sachant que C++ autorise la surcharge, vous pouvez appeler des surcharges de **asin** avec **float** et **long** **double** valeurs. Dans un programme C, **asin** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf**, **asinl**|\<math.h>|\<cmath> ou \<math.h>|

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
