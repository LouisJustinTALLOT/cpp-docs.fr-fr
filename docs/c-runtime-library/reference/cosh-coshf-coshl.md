---
title: cosh, coshf, coshl
ms.date: 04/11/2018
apiname:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 0f55e084e760cb6d04dbe7ec4fefb5e2ac1d79fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347442"
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

Le cosinus hyperbolique de *x*.

Par défaut, si le résultat est trop grand dans un **cosh**, **coshf**, ou **coshl** appeler, la fonction retourne **HUGE_VAL** et définit **errno** à **ERANGE**.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|none|**_DOMAIN**|
|*x* ≥ 7.104760e + 002|**INEXACT**+**OVERFLOW**|**OVERFLOW**|

## <a name="remarks"></a>Notes

Sachant que C++ autorise la surcharge, vous pouvez appeler des surcharges de **cosh** qui acceptent et retournent **float** ou **long** **double** valeurs. Dans un programme C, **cosh** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**coshf**, **cosl**, **coshl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [sinh, sinhf, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
