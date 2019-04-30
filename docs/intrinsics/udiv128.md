---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 0e66bbe978199f47134aa288bdd2bac4eb3e332a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390163"
---
# <a name="udiv128"></a>_udiv128

Le `_udiv128` intrinsèque divise un entier non signé 128 bits en un entier non signé 64 bits. La valeur de retour conserve le quotient, et la fonction intrinsèque retourne le reste à un paramètre de pointeur. `_udiv128` est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Paramètres

*highDividend* \
[in] 64 bits de poids fort du dividende.

*lowDividend* \
[in] 64 bits de poids faibles du dividende.

*divisor* \
[in] Entier 64 bits à diviser par.

*remainder* \
[out] Les bits d’entier 64 bits du reste.

## <a name="return-value"></a>Valeur de retour

Les 64 bits du quotient.

## <a name="remarks"></a>Notes

Passer les 64 bits supérieurs du dividende 128 bits dans *highDividend*et 64 bits de poids faible dans *lowDividend*. La fonction intrinsèque divise cette valeur en *diviseur*. Il stocke le reste de l’entier non signé 64 bits vers lequel pointé *reste*et retourne les 64 bits du quotient.

Le `_udiv128` intrinsèque est disponible à partir de Visual Studio 2019 RTM.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|Header|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>Voir aussi

[_div128](div128.md) \
[Intrinsèques du compilateur](compiler-intrinsics.md)
