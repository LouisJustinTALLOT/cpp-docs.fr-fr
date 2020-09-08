---
title: copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl
description: Référence d’API pour retourner une valeur qui a la grandeur d’un argument et le signe d’un autre à l’aide de copysign ()
ms.date: 9/1/2020
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 8f9ffe56e82f6a82da15fde3f8efea60fc1c0f9f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554862"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl

Retourne une valeur qui a la grandeur d’un argument et le signe d’un autre.

## <a name="syntax"></a>Syntaxe

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
#define copysign(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur à virgule flottante retournée en tant que grandeur du résultat.

*y*\
Valeur à virgule flottante retournée en tant que signe du résultat.

[Routines de prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>Valeur renvoyée

Les fonctions **copysign** retournent une valeur à virgule flottante qui combine l’amplitude de *x* et le signe de *y*. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **copysign** qui acceptent et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **copysign** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `copysign()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**, **copysignf**, **copysignl**, **_copysignf**, **_copysignl**|\<math.h>|
|**copysign** macro) | \<tgmath.h> |

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign, _chgsignf, _chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
