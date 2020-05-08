---
title: cosh, coshf, coshl
ms.date: 4/2/2020
api_name:
- cosh
- coshf
- coshl
- _o_cosh
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: e5e313f08fc7e6d00a1cffc9522d3c8a818cd152
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917227"
---
# <a name="cosh-coshf-coshl"></a>cosh, coshf, coshl

Calcule le cosinus hyperbolique.

## <a name="syntax"></a>Syntaxe

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Angle en radians.

## <a name="return-value"></a>Valeur de retour

Cosinus hyperbolique de *x*.

Par défaut, si le résultat est trop grand dans un appel **cosh**, **coshf,** ou **cosl** , la fonction retourne **HUGE_VAL** et définit **errno** sur **ERANGE**.

|Entrée|Exception SEH|Exception\{b\> \<b\}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Aucun|**_DOMAIN**|
|*x* ≥ 7.104760 e + 002|**INEXACT**+**dépassement de capacité** inexact|**SURCHARGE**|

## <a name="remarks"></a>Notes 

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **cosh** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, **cosh** prend toujours et retourne un **double**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**coshf,**, **COSL**, **COSL**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

Consultez l’exemple dans [Sinh, sinhf,, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
