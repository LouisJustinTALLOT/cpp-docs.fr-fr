---
title: fmin, fminf, fminl
ms.date: 04/05/2018
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: d6cd16c298c3f4bedb8064d66efd2d4bbe20c22b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216984"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Détermine la plus petite de deux valeurs spécifiées.

## <a name="syntax"></a>Syntaxe

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur à comparer.

*y*<br/>
Deuxième valeur à comparer.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur la plus petite de *x* ou *y*.

|Entrée|Résultats|
|-----------|------------|
|*x* est NaN|*y*|
|*y* est NaN|*x*|
|*x* et *y* sont des Nan|NaN|

La fonction ne provoque pas l’appel de [_matherr](matherr.md) , provoque des exceptions à virgule flottante ou modifie la valeur de **errno**.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **fmin,** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, **fmin,** accepte et retourne toujours un **`double`** .

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**fmin,**, **fminf,**, **fminl**|Secteur\<math.h><br />C++ : \<math.h> ou\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
