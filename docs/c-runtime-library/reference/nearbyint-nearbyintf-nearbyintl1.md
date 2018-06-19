---
title: nearbyint, nearbyintf, nearbyintl | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2362a68bf73a370f2fdf8eaa5ecb18b0a08bfaad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403233"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Arrondit la valeur à virgule flottante spécifiée en un entier et retourne cette valeur dans un format à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à arrondir.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne *x*, arrondi à l’entier le plus proche, à l’aide du format d’arrondi actuel comme indiqué par [fegetround](fegetround-fesetround2.md). Sinon, la fonction peut retourner l’une des valeurs suivantes :

|Problème|Retourner|
|-----------|------------|
|*x* = ±INFINITY|±Infinity, non modifié|
|*x* = ±0|±0, non modifié|
|*x* = NaN|NaN|

Les erreurs ne sont pas signalés via [_matherr](matherr.md); plus précisément, cette fonction ne signale pas les **FE_INEXACT** exceptions.

## <a name="remarks"></a>Notes

La principale différence entre cette fonction et [imprimer](rint-rintf-rintl.md) est que cette fonction ne déclenche pas l’exception à virgule flottante inexact.

Étant donné que les valeurs à virgule flottante maximales sont des entiers exacts, cette fonction ne provoque jamais de dépassement par elle-même. Cependant, la sortie peut dépasser la valeur de retour, selon la version de la fonction que vous utilisez.

C++ autorise la surcharge, vous pouvez appeler des surcharges de **nearbyint** qui acceptent et retournent **float** ou **long** **double** paramètres. Dans un programme C, **nearbyint** toujours accepte deux valeurs doubles et retourne une valeur double.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[Mathématiques et prise en charge à virgule flottante](../floating-point-support.md)<br/>
