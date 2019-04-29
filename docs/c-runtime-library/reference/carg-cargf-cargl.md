---
title: carg, cargf, cargl
ms.date: 11/04/2016
apiname:
- carg
- cargf
- cargl
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
ms.openlocfilehash: 584732594cd9ca9579907986e3dc3b5f3dbf52c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340714"
---
# <a name="carg-cargf-cargl"></a>carg, cargf, cargl

Récupère l’argument d’un nombre complexe, avec une coupure sur l’axe des réels négatifs.

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
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur de retour

L’argument (également appelé phase) de *z*. Le résultat est dans l’intervalle [-π, + π].

## <a name="remarks"></a>Notes

Étant donné que C++ autorisant la surcharge, vous pouvez appeler des surcharges de **carg** acceptant **_Fcomplex** ou **_Lcomplex** valeurs et retournent **float**ou **long** **double** valeurs. Dans un programme C, **carg** prend toujours un **_Dcomplex** valeur et retourne un **double** valeur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**carg**,               **cargf**, **cargl**|\<complex.h>|\<ccomplex>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
