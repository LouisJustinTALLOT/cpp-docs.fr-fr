---
description: 'En savoir plus sur : _scalb, _scalbf'
title: _scalb, _scalbf
ms.date: 1/15/2021
api_name:
- _scalb
- _scalbf
- _o__scalb
- _o__scalbf
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
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.openlocfilehash: da5a33bd6ed24ba0a3a58f789a9c8900910454d1
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98564080"
---
# <a name="_scalb-_scalbf"></a>`_scalb`, `_scalbf`

Met à l’échelle un argument par une puissance de 2.

## <a name="syntax"></a>Syntaxe

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante double précision.

*`exp`*\
Exposant entier long.

## <a name="return-value"></a>Valeur renvoyée

Retourne une valeur exponentielle en cas de réussite. En cas de dépassement (selon le signe de *`x`* ), **`_scalb`** retourne +/- **`HUGE_VAL`** ; la **`errno`** variable a la valeur **`ERANGE`** .

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarques

La **`_scalb`** fonction calcule la valeur de *`x`* \* 2 <sup>*`exp`*</sup> .

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`_scalb`**, **`_scalbf`**|`<float.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`ldexp`](ldexp.md)