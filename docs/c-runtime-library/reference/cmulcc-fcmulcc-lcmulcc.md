---
title: _Cmulcc, _FCmulcc, _LCmulcc | Documents Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1c4290c7e1f7a1ec917f2b2a197f787d28b9cd9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394982"
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

Multiplie deux nombres complexes.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Un des opérandes complexes à multiplier.

*y*<br/>
L’autre opérande complexe à multiplier.

## <a name="return-value"></a>Valeur de retour

A **_Dcomplex**, **_Fcomplex**, ou **_Lcomplex** structure qui représente le produit complexe de nombres complexes *x* et *y*.

## <a name="remarks"></a>Notes

Étant donné que les opérateurs arithmétiques intégrés ne fonctionnent pas sur l’implémentation Microsoft de types complexes, le **_Cmulcc**, **_FCmulcc**, et **_LCmulcc** fonctions simplifier la multiplication de types complexes.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**_Cmulcc**, **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

Ces fonctions sont spécifiques à Microsoft. Les types **_Dcomplex**, **_Fcomplex**, et **_Lcomplex** sont équivalents spécifiques à Microsoft pour les types natifs C99 non implémentées **_Complex double** , **float _Complex**, et **_Complex long double**, respectivement. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
