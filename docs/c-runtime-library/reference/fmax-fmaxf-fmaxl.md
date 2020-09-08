---
title: fmax, fmaxf, fmaxl
description: Informations de référence sur les API pour Fmax, fmaxf, et fmaxl ; qui détermine la plus grande de deux valeurs numériques.
ms.date: 9/1/2020
api_name:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 4f38db64b30598e7cfb4eb4d0f57dccf257dabc5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556682"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Déterminent la plus grande de deux valeurs numériques spécifiées.

## <a name="syntax"></a>Syntaxe

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

#define fmax(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Première valeur à comparer.

*y*\
Deuxième valeur à comparer.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne le plus grand de *x* ou *y*. La valeur retournée est exacte et ne dépend d’aucune forme d’arrondi.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = Nan|*y*|
|*y* = Nan|*x*|
|*x* et *y* = Nan|NaN|

Cette fonction n’utilise pas les erreurs spécifiées dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de Fmax qui acceptent et retournent des `float` `long double` types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, `fmax` prend et retourne toujours un double.

Si vous utilisez la \<tgmath.h> `fmax()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Function|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**Fmax**, **fmaxf,**, **fmaxl**|\<math.h>|\<cmath> ou \<math.h>|
|**Fmax** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
