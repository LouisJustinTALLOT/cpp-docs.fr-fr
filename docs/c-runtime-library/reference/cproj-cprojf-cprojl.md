---
title: cproj, cprojf, cprojl
description: Informations de référence sur les API pour cproj, cprojf et cprojl ; qui récupère la projection d’un nombre complexe sur la sphère Reimann.
ms.date: 9/2/2020
api_name:
- cproj
- cprojf
- cprojl
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
- cproj
- cprojf
- cprojl
- complex/cproj
- complex/cprojf
- complex/cprojl
helpviewer_keywords:
- cproj function
- cprojf function
- cprojl function
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
ms.openlocfilehash: fcc3c0a42c8c6392130ad58ed12c4985e7ad4907
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555941"
---
# <a name="cproj-cprojf-cprojl"></a>cproj, cprojf, cprojl

Récupère la projection d’un nombre complexe sur la sphère de Reimann.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex cproj(
   _Dcomplex z
);
_Fcomplex cproj(
   _Fcomplex z
);  // C++ only
_Lcomplex cproj(
   _Lcomplex z
);  // C++ only
_Fcomplex cprojf(
   _Fcomplex z
);
_Lcomplex cprojl(
   _Lcomplex z
);
#define cproj(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe.

## <a name="return-value"></a>Valeur renvoyée

Projection de *z* sur la sphère Reimann.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **cproj** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **cproj** accepte et retourne toujours une valeur **_Dcomplex** .

Si vous utilisez la \<tgmath.h> `cproj()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**cproj**, **cprojf**, **cprojl**|\<complex.h>|\<ccomplex>|
|**cproj** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
