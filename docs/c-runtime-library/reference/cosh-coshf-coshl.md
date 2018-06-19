---
title: COSH, coshf, coshl | Documents Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d77bb1d1b8f055bb4fe11d4c44c48fb3bf3be535
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395469"
---
# <a name="cosh-coshf-coshl"></a>COSH, coshf, coshl

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

Par défaut, si le résultat est trop volumineux dans un **cosh**, **coshf**, ou **coshl** appeler, la fonction retourne **HUGE_VAL** et définit **errno** à **ERANGE**.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|
|*x* ≥ 7.104760e + 002|**INEXACT**+**DE DÉPASSEMENT DE CAPACITÉ**|**DÉPASSEMENT DE CAPACITÉ**|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **cosh** qui acceptent et retournent **float** ou **long** **double** valeurs. Dans un programme C, **cosh** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis (C)|En-tête requis (C++)|
|-------------|---------------------|-|
|**coshf**, **cosl**, **coshl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple de [sinh, sinhf, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
