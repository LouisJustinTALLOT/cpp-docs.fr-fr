---
description: 'En savoir plus sur les éléments suivants : _Cbuild, _FCbuild _LCbuild'
title: _Cbuild, _FCbuild, _LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: bbca2571a10badcfc02da3e0d2f404590a1d7eb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275227"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Construit un nombre complexe à partir de parties réelles et imaginaires.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Paramètres

*real*<br/>
Partie réelle du nombre complexe à construire.

*imaginaire*<br/>
Partie imaginaire du nombre complexe à construire.

## <a name="return-value"></a>Valeur renvoyée

Structure **_Dcomplex**, **_Fcomplex** ou **_Lcomplex** qui représente le nombre complexe (i *réel*, *imaginaire* \* ) pour les valeurs du type à virgule flottante spécifié.

## <a name="remarks"></a>Notes

Les fonctions **_Cbuild**, **_FCbuild** et **_LCbuild** simplifient la création de types complexes. Utilisez les fonctions [CREAL, crealf, Creall](creal-crealf-creall.md) et [Cimag, cimagf, cimagl](cimag-cimagf-cimagl.md) pour récupérer les portions réelles et imaginaires des nombres complexes représentés.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild** **_LCbuild**|\<complex.h>|\<ccomplex>|

Ces fonctions sont spécifiques à Microsoft. Les types **_Dcomplex**, **_Fcomplex** et **_Lcomplex** sont des équivalents spécifiques à Microsoft des types natifs C99 non implémentés **`double _Complex`** , **`float _Complex`** et **`long double _Complex`** , respectivement. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
