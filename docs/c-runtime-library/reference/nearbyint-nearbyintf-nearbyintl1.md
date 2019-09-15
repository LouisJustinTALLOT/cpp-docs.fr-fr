---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
api_name:
- nearbyint
- nearbyintf
- nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: cd0a7d00c5019dd1e483d555df6db8d9770e61c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951390"
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

En cas de réussite, retourne *x*, arrondi à l’entier le plus proche, en utilisant le format d’arrondi actuel comme indiqué par [fegetround](fegetround-fesetround2.md). Sinon, la fonction peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* = ± infini|± INFINI, non modifié|
|*x* = ±0|± 0, non modifié|
|*x* = Nan|NaN|

Les erreurs ne sont pas signalées par _ [Mather](matherr.md); plus précisément, cette fonction ne signale aucune exception **FE_INEXACT** .

## <a name="remarks"></a>Notes

La principale différence entre cette fonction et l' [Imprimer](rint-rintf-rintl.md) est que cette fonction ne génère pas l’exception à virgule flottante inexacte.

Étant donné que les valeurs à virgule flottante maximales sont des entiers exacts, cette fonction ne provoque jamais de dépassement par elle-même. Cependant, la sortie peut dépasser la valeur de retour, selon la version de la fonction que vous utilisez.

C++autorise la surcharge, de sorte que vous pouvez appeler des surcharges de **nearbyint** qui acceptent et retournent des paramètres **float** ou **long** **double** . Dans un programme C, **nearbyint** accepte toujours deux valeurs de type double et retourne une valeur double.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[Prise en charge des fonctions mathématiques et à virgule flottante](../floating-point-support.md)<br/>
