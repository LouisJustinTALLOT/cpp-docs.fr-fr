---
title: cosh, coshf, coshl
ms.date: 04/11/2018
api_name:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 446988e67ca6e3b4a3839a9336f1ea4e2755c124
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938993"
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

Par défaut, si le résultat est trop grand dans un appel **cosh**, **coshf,** ou **COSL** , la fonction retourne **HUGE_VAL** et définit **errno** sur **ERANGE**.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|none|**_DOMAIN**|
|*x* ≥ 7.104760 e + 002|**INEXACT**+**OVERFLOW**|**OVERFLOW**|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **cosh** qui acceptent et retournent des valeurs **float** ou **long** **double** . Dans un programme C, **cosh** prend toujours et retourne un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**coshf**, **cosl**, **coshl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple dans [Sinh, sinhf,, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
