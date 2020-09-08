---
title: carg, cargf, cargl
description: Informations de référence sur les API pour carg, cargf et cargl ; qui récupère l’argument d’un nombre complexe, avec une coupure de branche le long de l’axe réel négatif.
ms.date: 9/2/2020
api_name:
- carg
- cargf
- cargl
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
- carg
- cargf
- cargl
- complex/carg
- complex/cargf
- complex/cargl
helpviewer_keywords:
- carg function
- cargf function
- cargl function
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
ms.openlocfilehash: 907694904b260c44dde84724c739c62dfe46dbde
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555811"
---
# <a name="carg-cargf-cargl"></a>carg, cargf, cargl

Récupère l’argument d’un nombre complexe, avec une coupure de branche le long de l’axe réel négatif.

## <a name="syntax"></a>Syntaxe

```C
double carg(
   _Dcomplex z
);
float carg(
   _Fcomplex z
);  // C++ only
long double carg(
   _Lcomplex z
);  // C++ only
float cargf(
   _Fcomplex z
);
long double cargl(
   _Lcomplex z
);
#define carg(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe.

## <a name="return-value"></a>Valeur renvoyée

Argument (également appelé phase) de *z*. Le résultat est dans l’intervalle [-π, + π].

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **carg** qui acceptent des valeurs **_Fcomplex** ou **_Lcomplex** , et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **carg** prend toujours une valeur **_Dcomplex** et retourne une **`double`** valeur.

Si vous utilisez la \<tgmath.h> `carg()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**carg**, **cargf**, **cargl**|\<complex.h>|\<ccomplex>|
|**carg** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
