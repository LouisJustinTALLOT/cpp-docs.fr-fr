---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 4/2/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338590"
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

*X*<br/>
Valeur à arrondir.

## <a name="return-value"></a>Valeur de retour

En cas de succès, retourne *x*, arrondi à l’intégrateur le plus proche, en utilisant le format d’arrondissement actuel tel que rapporté par [fegetround](fegetround-fesetround2.md). Sinon, la fonction peut retourner l’une des valeurs suivantes :

|Problème|Renvoie|
|-----------|------------|
|*x* ' 'INFINITY'|L’INFINITY, non modifié|
|*x* 0 euros|0, non modifié|
|*x* NaN|NaN|

Les erreurs ne sont pas signalées par [_matherr](matherr.md); spécifiquement, cette fonction ne signale aucune **FE_INEXACT** exceptions.

## <a name="remarks"></a>Notes

La principale différence entre cette fonction et [le rint](rint-rintf-rintl.md) est que cette fonction ne soulève pas l’exception de point flottant inexact.

Étant donné que les valeurs à virgule flottante maximales sont des entiers exacts, cette fonction ne provoque jamais de dépassement par elle-même. Cependant, la sortie peut dépasser la valeur de retour, selon la version de la fonction que vous utilisez.

Le CMD permet la surcharge, de sorte que vous pouvez appeler des surcharges de **nearbyint** qui prennent et retournent **flotteur** ou **longs** paramètres **doubles.** Dans un programme C, **nearbyint** prend toujours deux doubles valeurs et retourne une double valeur.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> ou \<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[Prise en charge des fonctions mathématiques et à virgule flottante](../floating-point-support.md)<br/>
