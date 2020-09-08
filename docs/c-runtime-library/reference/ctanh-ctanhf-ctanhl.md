---
title: ctanh, ctanhf, ctanhl
description: Informations de référence sur l’API pour ctanh, ctanhf, ctanhl ; calcule la tangente hyperbolique complexe d’un nombre complexe.
ms.date: 11/04/2016
api_name:
- ctanh
- ctanhf
- ctanhl
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
- ctanh
- ctanhf
- ctanhl
- complex/ctanh
- complex/ctanhf
- complex/ctanhl
helpviewer_keywords:
- ctanh function
- ctanhl function
- ctanhf function
ms.assetid: 807f2cd1-8740-4988-afff-5911c346385b
ms.openlocfilehash: 959d48853e3edac707a7daea615270b20dad37e7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555864"
---
# <a name="ctanh-ctanhf-ctanhl"></a>ctanh, ctanhf, ctanhl

Calcule la tangente hyperbolique complexe d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex ctanh(
   _Dcomplex z
);
_Fcomplex ctanh(
   _Fcomplex z
);  // C++ only
_Lcomplex ctanh(
   _Lcomplex z
);  // C++ only
_Fcomplex ctanhf(
   _Fcomplex z
);
_Lcomplex ctanhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe qui représente un angle, en radians.

## <a name="return-value"></a>Valeur renvoyée

Tangente hyperbolique complexe de *z*.

|Entrée|Exception SEH|**_matherr** Titre|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|aucun|_DOMAIN|
|± ∞ (Tan, Tanf,)|NON VALIDE|_DOMAIN|

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ctanh** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, **ctanh** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**ctanh**,               **ctanhf**, **ctanhl**|\<complex.h>|\<ccomplex>|

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
