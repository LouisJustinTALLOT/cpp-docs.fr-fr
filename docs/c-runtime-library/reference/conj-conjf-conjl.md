---
title: conj, conjf, conjl
description: Informations de référence sur les API pour conj, conjf et conjl ; qui récupèrent le conjugué complexe d’un nombre complexe.
ms.date: 9/2/2020
api_name:
- conj
- conjf
- conjl
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
- conj
- conjf
- conjl
- complex/conj
- complex/conjf
- complex/conjl
helpviewer_keywords:
- conj function
- conjf function
- conjl function
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
ms.openlocfilehash: b779eb2d92893b204a73b2fa4f5c89928933ffeb
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556351"
---
# <a name="conj-conjf-conjl"></a>conj, conjf, conjl

Récupère le conjugué complexe d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex conj(
   _Dcomplex z
);
_Fcomplex conj(
   _Fcomplex z
);  // C++ only
_Lcomplex conj(
   _Lcomplex z
);  // C++ only
_Fcomplex conjf(
   _Fcomplex z
);
_Lcomplex conjl(
   _Lcomplex z
);
#define conj(X) // Requires C11 or higher
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe.

## <a name="return-value"></a>Valeur renvoyée

Conjugué complexe de *z*.  Le résultat a la même partie réelle et imaginaire que *z*, mais avec le signe opposé.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **conj** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, à moins que vous n’utilisiez la \<tgmath.h> macro pour appeler cette fonction, **conj** accepte et retourne toujours une valeur **_Dcomplex** .

Si vous utilisez la \<tgmath.h> `conj()` macro, le type de l’argument détermine la version de la fonction qui est sélectionnée. Pour plus d’informations [, consultez Math type-Generic](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**conj**, **conjf**, **conjl**|\<complex.h>|\<ccomplex>|
|**conj** macro) | \<tgmath.h> ||

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
