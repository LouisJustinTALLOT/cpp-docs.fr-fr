---
title: cacos, cacosf, cacosl
ms.date: 11/04/2016
api_name:
- cacos
- cacosf
- cacosl
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
- cacos
- cacosf
- cacosl
- complex/cacos
- complex/cacosf
- complex/cacosl
helpviewer_keywords:
- cacos function
- cacosf function
- cacosl function
ms.assetid: 78118c00-0a07-49c1-8a13-4bf19ce3aea8
ms.openlocfilehash: 5b0751703b9b9cdcdb50e265a6b5d3c929d89ae1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939398"
---
# <a name="cacos-cacosf-cacosl"></a>cacos, cacosf, cacosl

Récupère l’arc cosinus d’un nombre complexe, avec des coupes en dehors de l’intervalle [-1, + 1] le long de l’axe réel.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex cacos( _Dcomplex z );
_Fcomplex cacosf( _Fcomplex z );
_Lcomplex cacosl( _Lcomplex z );
```

```cpp
_Fcomplex cacos( _Fcomplex z );  // C++ only
_Lcomplex cacos( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Paramètres

*z*<br/>
Nombre complexe qui représente un angle, en radians.

## <a name="return-value"></a>Valeur de retour

Arccosinus de *z*, en radians. Le résultat est illimité le long de l’axe imaginaire, et dans l’intervalle [0, π] le long de l’axe réel. Une erreur de domaine se produit si *z* est en dehors de l’intervalle [-1, + 1].

## <a name="remarks"></a>Notes

Étant C++ donné que autorise la surcharge, vous pouvez appeler des surcharges de **Cacos** qui acceptent et retournent des valeurs **_Fcomplex** et **_Lcomplex** . Dans un programme C, **Cacos** accepte et retourne toujours une valeur **_Dcomplex** .

## <a name="requirements"></a>Configuration requise

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**cacos**,               **cacosf**, **cacosl**|\<complex.h>|\<ccomplex>|

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
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
