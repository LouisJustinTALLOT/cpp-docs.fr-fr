---
title: creal, crealf, creall
description: Informations de référence sur l’API pour CREAL, crealf, Creall ; qui récupère la partie réelle d’un nombre complexe.
ms.date: 9/2/2020
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4f375bbe8813ba67130f8b56d8e2c99d5b734764
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555928"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Récupère la partie réelle d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
#define creal(X) // Requires C11 or higher

float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*Lettre*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur renvoyée

La partie réelle de *z*.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **CREAL** qui acceptent des valeurs **_Fcomplex** ou **_Lcomplex** , et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **CREAL** prend toujours une valeur **_Dcomplex** et retourne une **`double`** valeur.

Si vous utilisez la \<tgmath.h> `creal()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**CREAL**, **crealf**, **Creall**|\<complex.h>|\<ccomplex>|
|**CREAL** macro) | \<tgmath.h> ||

Les types de **_Fcomplex**, **_Dcomplex**et **_Lcomplex** sont des équivalents propres à Microsoft des types C99 natifs, **float _Complex**, **double _Complex**et **long double _Complex**, respectivement. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
