---
title: clog10, clog10f, clog10l
ms.date: 11/04/2016
api_name:
- clog10
- clog10f
- clog10l
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
- clog10
- clog10f
- clog10l
- complex/clog10
- complex/clog10f
- complex/clog10l
helpviewer_keywords:
- clog10 function
- clog10f function
- clog10l function
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
ms.openlocfilehash: a840494caf3c34f09d8c90970988e847be712cb4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939117"
---
# <a name="clog10-clog10f-clog10l"></a>clog10, clog10f, clog10l

Récupère le logarithme de base 10 d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex clog10( _Dcomplex z );
_Fcomplex clog10f( _Fcomplex z );
_Lcomplex clog10l( _Lcomplex z );
```

```cpp
_Fcomplex clog10( _Fcomplex z );  // C++ only
_Lcomplex clog10( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Base du logarithme.

## <a name="return-value"></a>Valeur de retour

Les valeurs de retour possibles sont :

|Paramètre z|Valeur de retour|
|-----------------|------------------|
|Positif|Logarithme de base 10 de z|
|Zéro|- ∞|
|Négatif|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **clog10** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, **clog10** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**clog10**,               **clog10f**, **clogl**|\<complex.h>|\<ccomplex>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog, clogf, clogl](clog-clogf-clogl.md)<br/>
