---
title: asin, asinf, asinl
ms.date: 4/2/2020
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
ms.openlocfilehash: cfee30270b8ed0daa5d600fec65659fbf07162fd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909268"
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

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**Non valide**|**_DOMAIN**|
|± **QNAN**, **IND**|Aucun|**_DOMAIN**|
|&#124;x&#124;>1|**Non valide**|**_DOMAIN**|

## <a name="remarks"></a>Notes 

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ASIN** avec des valeurs **float** et **long** **double** . Dans un programme C, **ASIN** prend toujours et retourne un **double**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**ASIN**, **ASInf,**, **asinl**|\<math.h>|\<cmath> ou \<math.h>|

## <a name="example"></a> Exemple

Pour plus d’informations, consultez [acos, acosf, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
