---
title: _Cbuild, _FCbuild, _LCbuild | Documents Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
dev_langs:
- C++
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6d567dc02715b9e55644b755b6d7360f2fe3d37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394385"
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Construit un nombre complexe à partir de parties réelles et imaginaires.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Paramètres

*real*<br/>
La partie réelle du nombre complexe à construire.

*partie imaginaire*<br/>
La partie imaginaire du nombre complexe à construire.

## <a name="return-value"></a>Valeur de retour

A **_Dcomplex**, **_Fcomplex**, ou **_Lcomplex** structure qui représente le nombre complexe (*réel*, *imaginaire*  \* i) pour les valeurs du type à virgule flottante spécifié.

## <a name="remarks"></a>Notes

Le **_Cbuild**, **_FCbuild**, et **_LCbuild** fonctions simplifient la création de types complexes. Utilisez le [creal, crealf, creall](creal-crealf-creall.md) et [cimag, cimagf, cimagl](cimag-cimagf-cimagl.md) fonctions pour récupérer les parties réelles et imaginaires des nombres complexes représentés.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex>|

Ces fonctions sont spécifiques à Microsoft. Les types **_Dcomplex**, **_Fcomplex**, et **_Lcomplex** sont équivalents spécifiques à Microsoft pour les types natifs C99 non implémentées **_Complex double** , **float _Complex**, et **_Complex long double**, respectivement. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
