---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946210"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Détermine la fonction gamma de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur dont le gamma doit être trouvé.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur gamma de *x*.

Une erreur de plage peut se produire si l’amplitude de *x* est trop grande ou trop petite pour le type de données. Une erreur de domaine ou une erreur de plage peut se produire si *x* < = 0.

|Problème|Renvoie|
|-----------|------------|
|x = ±0|± INFINI|
|x = entier négatif|NaN|
|x = -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|Erreur de domaine|NaN|
|erreur de pôle|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|
|erreur de plage avec dépassement de capacité positif|± HUGE_VAL, ± HUGE_VALF ou ± HUGE_VALL|
|erreur de plage avec dépassement de capacité négatif|valeur correcte après arrondi|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **tgamma** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **tgamma** accepte et retourne toujours un **double**.

Si x est un nombre naturel, cette fonction retourne la factorielle de (x-1).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**,  **tgammal**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
