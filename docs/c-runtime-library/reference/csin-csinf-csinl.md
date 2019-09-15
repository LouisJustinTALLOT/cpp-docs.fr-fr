---
title: csin, csinf, csinl
ms.date: 11/04/2016
api_name:
- csin
- csinf
- csinl
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
- csin
- csinf
- csinl
- complex/csin
- complex/csinf
- complex/csinl
helpviewer_keywords:
- csin function
- csinf function
- csinl function
ms.assetid: 3ed475e8-9aae-42ba-a25c-7ae656a0fd4d
ms.openlocfilehash: c0e0c57596ac36dbe3c0b72f79177b8df7b15af0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941982"
---
# <a name="csin-csinf-csinl"></a>csin, csinf, csinl

Récupère le sinus d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex csin(
   _Dcomplex z
);
_Fcomplex csin(
   _Fcomplex z
);  // C++ only
_Lcomplex csin(
   _Lcomplex z
);  // C++ only
_Fcomplex csinf(
   _Fcomplex z
);
_Lcomplex csinl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe qui représente un angle, en radians.

## <a name="return-value"></a>Valeur de retour

Sinus de *z*, en radians.

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **CSIN** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, **CSIN** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**csin**,               **csinf**, **csinl**|\<complex.h>|\<ccomplex>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
