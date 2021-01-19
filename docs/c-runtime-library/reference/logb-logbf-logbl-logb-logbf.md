---
title: logb, logbf, logbl, _logb, _logbf
description: Informations de référence sur les API pour logb, logbf, logbl, _logb et _logbf ; qui extraient la valeur d’exposant d’un argument à virgule flottante.
ms.date: 1/15/2021
api_name:
- logb
- _logb
- _logbl
- logbf
- _logbf
- logbl
- _o__logb
- _o_logb
- _o_logbf
- _o_logbl
- _o__logbf
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.openlocfilehash: 5d64b315a502f7d1794d7726f14a94ed66a67cd5
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564028"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>`logb`, `logbf`, `logbl`, `_logb`, `_logbf`

Extrait la valeur d’exposant d’un argument à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
#define logb(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

**`logb`** retourne la valeur d’exposant non biaisée de *`x`* sous la forme d’un entier signé représenté sous la forme d’une valeur à virgule flottante.

## <a name="remarks"></a>Remarques

Les **`logb`** fonctions extraient la valeur exponentielle de l’argument à virgule flottante *`x`* , comme si *`x`* elles étaient représentées par une plage infinie. Si l’argument *`x`* est dénormalisé, il est traité comme s’il était normalisé.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **`logb`** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la `<tgmath.h>` macro pour appeler cette fonction, **`logb`** accepte et retourne toujours un **`double`** .

Si vous utilisez la `<tgmath.h>` `logb()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

|Entrée|Exception SEH|`Matherr` titre|
|-----------|-------------------|-----------------------|
|`± QNAN`,`IND`|None|`_DOMAIN`|
|± 0|`ZERODIVIDE`|`_SING`|

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`_logb`**|`<float.h>`|
|**`logb`**, **`logbf`**, **`logbl`**, **`_logbf`**|`<math.h>`|
|**`logb`** macrovirus | `<tgmath.h>` |

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`frexp`](frexp.md)