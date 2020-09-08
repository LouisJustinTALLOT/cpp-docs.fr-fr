---
title: expm1, expm1f, expm1l
description: Informations de référence sur les API pour expm1, expm1f et expm1 ; qui calcule la valeur exponentielle de base e d’une valeur, moins un.
ms.date: 9/1/2020
api_name:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 6d352e91d895cd63c7134faff90bc1bc43a50708
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556500"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Calcule l’exponentielle de base e d’une valeur, moins 1.

## <a name="syntax"></a>Syntaxe

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
#define expm1(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur exponentielle à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **expm1** retournent une valeur à virgule flottante qui représente e<sup>x</sup> -1, en cas de réussite. En cas de dépassement de capacité, **expm1** retourne **HUGE_VAL**, **expm1f** retourne **HUGE_VALF**, **expm1l** retourne **HUGE_VALL**et **errno** a la valeur **ERANGE**. Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **expm1** qui acceptent et retournent des **`float`** **`long double`** valeurs et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **expm1** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `expm1()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**expm1**, **expm1f**, **expm1l**|\<math.h>|
|**expm1** macro) | \<tgmath.h> |

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
