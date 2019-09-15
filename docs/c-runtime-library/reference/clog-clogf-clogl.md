---
title: clog, clogf, clogl
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 76ee6e4e81c275c8cbed0f74914521c0b44499bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942923"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Récupère le logarithme népérien d’un nombre complexe, avec une coupure sur l’axe des réels négatifs.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Base du logarithme.

## <a name="return-value"></a>Valeur de retour

Logarithme népérien de *z*. Le résultat est illimité le long de l’axe réel et dans l’intervalle [-Iπ, + Iπ] le long de l’axe imaginaire.

Les valeurs de retour possibles sont :

|Paramètre z|Valeur de retour|
|-----------------|------------------|
|Positif|Logarithme de base 10 de z|
|Zéro|- ∞|
|Négatif|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges d' **encombrements** qui prennent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, le **colmatage** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**clog**,               **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
