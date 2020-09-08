---
title: cexp, cexpf, cexpl
description: Informations de référence sur les API pour cexp, cexpf et cexpl ; qui calcule la valeur exponentielle de base e d’un nombre complexe.
ms.date: 11/04/2016
api_name:
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
ms.openlocfilehash: 66f7b687e8da12473abef4dbc44831e175956ac0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555213"
---
# <a name="cexp-cexpf-cexpl"></a>cexp, cexpf, cexpl

Calcule la valeur exponentielle de base e d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex cexp( _Dcomplex z );
_Fcomplex cexpf( _Fcomplex z );
_Lcomplex cexpl( _Lcomplex z );

_Fcomplex cexp( _Fcomplex z );  // C++ only
_Lcomplex cexp( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*Lettre*\
Nombre complexe qui représente l’exposant.

## <a name="return-value"></a>Valeur renvoyée

Valeur de **e** élevée à la puissance de *z*.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **cexp** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, **cexp** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**cexp**, **cexpf**, **cexpl**|\<complex.h>|\<complex.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)\
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)\
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)\
[clog, clogf, clogl](clog-clogf-clogl.md)
