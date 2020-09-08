---
title: log1p, log1pf, log1pl2
description: Informations de référence sur l’API pour log1p, log1pf, log1pl2 ; qui calcule le logarithme népérien de 1 plus la valeur spécifiée.
ms.date: 9/1/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: 8858d761428d4dad6e3fe836b82041ae92f1827a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556228"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Calcule le logarithme népérien de 1 plus la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double log1p(
   double x
);
float log1pf(
   float x
);
long double log1pl(
   long double x
);

#define log1p(X) // Requires C11 or higher

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*\
Argument à virgule flottante.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne le logarithme naturel (base-*e*) de (*x* + 1).

Sinon, peut retourner l’une des valeurs suivantes :

|Entrée|Résultats|Exception SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Nombres dénormalisés|Comme dans l’entrée|UNDERFLOW||
|± 0|Comme dans l’entrée|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NaN|NON VALIDE|EDOM|
|-inf|NaN|NON VALIDE|EDOM|
|± SNaN|Comme dans l’entrée|NON VALIDE||
|± QNaN, indéfini|Comme dans l’entrée|||

La valeur **errno** est définie sur ERANGE si *x* =-1. La valeur **errno** est définie sur **EDOM** si *x* <-1.

## <a name="remarks"></a>Notes

Les fonctions **log1p** peuvent être plus précises que l’utilisation de `log(x + 1)` lorsque *x* est proche de 0.

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **log1p** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **log1p** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `log1p()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

Si *x* est un nombre naturel, cette fonction retourne le logarithme de la factorielle de (*x* -1).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|
|**log1p** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)\
[Log2, log2f,, log2l](log2-log2f-log2l.md)\
[log, logf, log10, log10f](log-logf-log10-log10f.md)
