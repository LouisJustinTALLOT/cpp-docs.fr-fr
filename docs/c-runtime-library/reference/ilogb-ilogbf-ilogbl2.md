---
title: ilogb, ilogbf, ilogbl2
description: Informations de référence sur les API pour ilogb, ilogbf et ilogbl2 ; qui récupère un entier qui représente l’exposant de base 2 non biaisé de la valeur spécifiée.
ms.date: 9/1/2020
api_name:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: b27c329cca1edb9d30bb6b9b641f94d174c9c406
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556370"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Récupère un entier qui représente l’exposant en base 2 non biaisé de la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);

#define ilogbl(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*x*\
Valeur spécifiée.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne l’exposant de base 2 de *x* en tant que **`signed int`** valeur.

Sinon, retourne l’une des valeurs suivantes, définies dans \<math.h> :

|Entrée|Résultats|
|-----------|------------|
|± 0|FP_ILOGB0|
|+ INF, ± Nan, indéfini|FP_ILOGBNAN|

Les erreurs sont signalées comme indiqué dans [_matherr](matherr.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ilogb** qui acceptent et retournent des **`float`** **`long double`** types et. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **ilogb** accepte et retourne toujours un **`double`** .

Si vous utilisez la \<tgmath.h> `ilogb()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

L’appel de cette fonction est similaire à l’appel de la fonction **logb** équivalente, puis au cast de la valeur de retour en **`int`** .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**ilogb**, **ilogbf**, **ilogbl**|\<math.h>|\<cmath>|
|**ilogb** macro) | \<tgmath.h> ||

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
