---
title: ccosh, ccoshf, ccoshl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- ccosh
- ccoshf
- ccoshl
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
- ccosh
- ccoshf
- ccoshl
- complex/ccosh
- complex/ccoshf
- complex/ccoshl
dev_langs:
- C++
helpviewer_keywords:
- ccosh function
- ccoshf function
- ccoshl function
ms.assetid: 79667449-4edf-4948-bf6b-720adf2b3f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a883869b830efbba08822b77c97fd6a156358dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394481"
---
# <a name="ccosh-ccoshf-ccoshl"></a>ccosh, ccoshf, ccoshl

Récupère le cosinus hyperbolique d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex ccosh(
   _Dcomplex z
);
_Fcomplex ccosh(
   _Fcomplex z
);  // C++ only
_Lcomplex ccosh(
   _Lcomplex z
);  // C++ only
_Fcomplex ccoshf(
   _Fcomplex z
);
_Lcomplex ccoshl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe qui représente l’angle, en radians.

## <a name="return-value"></a>Valeur de retour

Le cosinus hyperbolique de *z*, en radians.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ccosh** qui acceptent et retournent **_Fcomplex** et **_Lcomplex** valeurs. Dans un programme C, **ccosh** accepte et retourne toujours un **_Dcomplex** valeur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**ccosh**, **ccoshf**, **ccoshl**|\<complex.h>|\<ccomplex>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
