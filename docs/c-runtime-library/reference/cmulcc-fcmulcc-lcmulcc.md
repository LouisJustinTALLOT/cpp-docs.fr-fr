---
title: _Cmulcc, _FCmulcc, _LCmulcc
ms.date: 03/30/2018
api_name:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: fc21f8cbd2103993bc2b3e36020c57c8520f04a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939073"
---
# <a name="_cmulcc-_fcmulcc-_lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

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
Autre opérande complexe à multiplier.

## <a name="return-value"></a>Valeur de retour

Structure **_Dcomplex**, **_Fcomplex**ou **_Lcomplex** qui représente le produit complexe des nombres complexes *x* et *y*.

## <a name="remarks"></a>Notes

Étant donné que les opérateurs arithmétiques intégrés ne fonctionnent pas sur l’implémentation Microsoft des types complexes, les fonctions **_Cmulcc**, **_FCmulcc**et **_LCmulcc** simplifient la multiplication des types complexes.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**_Cmulcc**, **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

Ces fonctions sont spécifiques à Microsoft. Les types **_Dcomplex**, **_Fcomplex**et **_Lcomplex** sont des équivalents spécifiques de Microsoft aux types natifs C99 non implémentés **double _Complex**, **float _Complex**et **long double _Complex**, respectivement. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
