---
description: 'En savoir plus sur les éléments suivants : _Cmulcr, _FCmulcr _LCmulcr'
title: _Cmulcr, _FCmulcr, _LCmulcr
ms.date: 03/30/2018
api_name:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
ms.openlocfilehash: ea1dbbcea6890246b1e318da238fb8cc2ee3abb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260720"
---
# <a name="_cmulcr-_fcmulcr-_lcmulcr"></a>_Cmulcr, _FCmulcr, _LCmulcr

Multiplie un nombre complexe par un nombre à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Un des opérandes complexes à multiplier.

*y*<br/>
Opérande à virgule flottante à multiplier.

## <a name="return-value"></a>Valeur renvoyée

Structure **_Dcomplex**, **_Fcomplex** ou **_Lcomplex** qui représente le produit complexe du nombre complexe *x* et du nombre de points flaoting *y*.

## <a name="remarks"></a>Notes

Étant donné que les opérateurs arithmétiques intégrés ne fonctionnent pas sur l’implémentation Microsoft des types complexes, les fonctions **_Cmulcr**, **_FCmulcr** et **_LCmulcr** simplifient la multiplication des types complexes par les types à virgule flottante.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**_Cmulcr**, **_FCmulcr** **_LCmulcr**|\<complex.h>|\<complex.h>|

Ces fonctions sont spécifiques à Microsoft. Les types **_Dcomplex**, **_Fcomplex** et **_Lcomplex** sont des équivalents propres à Microsoft pour les types natifs C99 **double _Complex**, **float _Complex** et **long double _Complex**, respectivement. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
