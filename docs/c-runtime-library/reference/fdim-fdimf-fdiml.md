---
title: fdim, fdimf, fdiml
ms.date: 04/05/2018
api_name:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 74935f724b678b08e39604d9916c7c5de5925aee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941299"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Détermine la différence positive entre les première et deuxième valeurs.

## <a name="syntax"></a>Syntaxe

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur.

*y*<br/>
Seconde valeur.

## <a name="return-value"></a>Valeur de retour

Retourne la différence positive entre *x* et *y*:

|Valeur de retour|Scénario|
|------------------|--------------|
|x-y|Si x > y|
|0|Si x <= y|

Sinon, peut retourner l’une des erreurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|Erreur de plage avec dépassement|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erreur de plage avec soupassement|valeur correcte (après arrondi)|
|*x* ou *y* est NaN|NaN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **FDIM** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **FDIM** accepte et retourne toujours un **double**.

À l’exception de la gestion NaN, cette fonction est `fmax(x - y, 0)`équivalente à.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fdim**, **fdimf**, **fdiml**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
