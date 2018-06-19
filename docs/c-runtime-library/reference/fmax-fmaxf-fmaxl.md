---
title: fmax, fmaxf, fmaxl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fmax
- fmaxf
- fmaxl
apilocation:
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
apitype: DLLExport
f1_keywords:
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs:
- C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6e210fac83c19efaecb909d54734d0422956f37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399814"
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

```

### <a name="parameters"></a>Paramètres

*x*<br/>
Première valeur à comparer.

*y*<br/>
Deuxième valeur à comparer.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne le plus grand de *x* ou *y*. La valeur retournée est exacte et ne dépend d’aucune forme d’arrondi.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Retourner|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* et *y* = NaN|NaN|

Cette fonction n’utilise pas les erreurs spécifiées dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de fmax qui acceptent et retournent des types double long et à virgule flottante. Dans un programme C, fmax accepte et retourne toujours un double.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**Fmax**, **fmaxf**, **fmaxl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
