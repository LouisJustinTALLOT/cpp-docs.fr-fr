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
ms.openlocfilehash: df01f2205291920b8c0519db622c93048278beb1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957091"
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

|Entrée|Résultat|
|-----------|------------|
|*x* est NaN|*y*|
|*y* est NaN|*x*|
|*x* et *y* sont des Nan|NaN|

La fonction ne provoque pas l’appel de _ [matherr](matherr.md) , provoquer des exceptions à virgule flottante ou modifier la valeur de **errno**.

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **fmin,** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **fmin,** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**fmin**, **fminf**, **fminl**|C : \<math.h><br />C++ : \<math.h> ou \<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
