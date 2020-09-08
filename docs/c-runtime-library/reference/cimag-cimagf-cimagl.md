---
title: cimag, cimagf, cimagl
description: Informations de référence sur les API pour Cimag, cimagf et cimagl ; qui récupère la partie imaginaire d’un nombre complexe.
ms.date: 9/2/2020
api_name:
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
ms.openlocfilehash: 41631a161a47e247b12a39e312a3f40084c8f22f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555838"
---
# <a name="cimag-cimagf-cimagl"></a>cimag, cimagf, cimagl

Récupère la partie imaginaire d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double cimag( _Dcomplex z );
float cimagf( _Fcomplex z );
long double cimagl( _Lcomplex z );
#define cimag(X) // Requires C11 or higher

float cimag( _Fcomplex z );  // C++ only
long double cimag( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe.

## <a name="return-value"></a>Valeur renvoyée

Partie imaginaire de *z*.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **Cimag** qui acceptent des valeurs **_Fcomplex** ou **_Lcomplex** , et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **Cimag** prend toujours une valeur **_Dcomplex** et retourne une **`double`** valeur.

Si vous utilisez la \<tgmath.h> `cimag()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**Cimag**, **cimagf**, **cimagl**|\<complex.h>|\<ccomplex>|
|**Cimag** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
