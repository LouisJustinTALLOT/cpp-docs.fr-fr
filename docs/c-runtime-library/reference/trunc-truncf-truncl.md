---
title: trunc, truncf, truncl
ms.date: 04/05/2018
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: b0c615c91e562fa45f791d8cc20f39a830013aeb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946004"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Détermine l’entier le plus proche dont la valeur est inférieure ou égale à la valeur à virgule flottante spécifiée.

## <a name="syntax"></a>Syntaxe

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à tronquer.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne une valeur entière de *x*, arrondie à zéro.

Sinon, peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = ± infini|x|
|*x* =  ±0|x|
|*x* = Nan|NaN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **trunc** qui acceptent et retournent des types **float** et **long** **double** . Dans un programme C, **trunc** prend toujours et retourne un **double**.

Comme les valeurs à virgule flottante les plus grandes sont des entiers exacts, cette fonction ne provoque pas de dépassement de capacité. Cependant, vous pouvez causer le dépassement de capacité de la fonction en retournant une valeur sous dans un type entier.

Vous pouvez aussi arrondir vers le bas en convertissant de manière implicite une valeur à virgule flottante en entier ; cependant, cette opération se limite aux valeurs qui peuvent être stockées dans le type cible.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**trunc**, **truncf**, **truncl**|\<math.h>|\<cmath>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
