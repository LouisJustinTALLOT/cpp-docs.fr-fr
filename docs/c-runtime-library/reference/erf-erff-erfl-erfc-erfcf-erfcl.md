---
title: erf, erff, erfl, erfc, erfcf, erfcl
description: Informations de référence sur l’API pour ERF, ERFF, erfl, ERFC, erfcf et erfcl ; qui calcule la fonction d’erreur ou la fonction d’erreur complémentaire d’une valeur.
ms.date: 9/1/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ef83275515c66341798395bbfc2bb5b088e6cfb7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555642"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Calcule la fonction d'erreur ou la fonction d'erreur complémentaire d'une valeur.

## <a name="syntax"></a>Syntaxe

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
#define erf(X) // Requires C11 or higher
#define erfc(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **ERF** retournent la fonction d’erreur Gauss de *x*. Les fonctions **ERFC** retournent la fonction d’erreur Gauss complémentaire de *x*.

## <a name="remarks"></a>Notes

Les fonctions **ERF** calculent la fonction d’erreur Gauss de *x*, qui est définie comme suit :

![Fonction d'erreur de x](media/crt_erf_formula.PNG "Fonction d'erreur de x")

La fonction d’erreur Gauss complémentaire est définie comme 1-ERF (x). Les fonctions **ERF** retournent une valeur comprise entre-1,0 et 1,0. Il n’y a pas d’erreur de retour. Les fonctions **ERFC** retournent une valeur comprise dans la plage 0 à 2. Si *x* est trop grand pour **ERFC**, la variable **errno** est définie sur **ERANGE**.

C++ autorisant la surcharge, vous pouvez appeler des surcharges d' **ERF** et **ERFC** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **ERF** et **ERFC** prennent toujours et retournent un **`double`** .

Si vous utilisez la \<tgmath.h> `erf()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**ERF**, **ERFF**, **erfl**, **ERFC**, **erfcf**, **erfcl**|\<math.h>|
|**ERF** , macro | \<tgmath.h> |

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
