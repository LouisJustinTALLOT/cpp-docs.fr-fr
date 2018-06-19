---
title: creal, crealf, creall | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
dev_langs:
- C++
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8d3ca02aeb0f3f9b12c8b82cbb27d9bd3ad3aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400858"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Récupère la partie réelle d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur de retour

La partie réelle de *z*.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **creal** acceptant **_Fcomplex** ou **_Lcomplex** valeurs et retournent **float** ou **long double** valeurs. Dans un programme C, **creal** prend toujours un **_Dcomplex** valeur et retourne un **double** valeur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**creal**, **crealf**, **creall**|\<complex.h>|\<ccomplex>|

Le **_Fcomplex**, **_Dcomplex**, et **_Lcomplex** types sont équivalents spécifiques à Microsoft des types natifs C99 non implémentées **float _Complex** , **_Complex double**, et **_Complex long double**, respectivement. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>