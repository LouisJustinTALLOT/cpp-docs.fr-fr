---
description: 'En savoir plus sur : _variant_t opérateurs relationnels'
title: _variant_t, opérateurs relationnels
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: 0a9c339bc67527e258c0d1f69060cde251c8adb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161427"
---
# <a name="_variant_t-relational-operators"></a>_variant_t, opérateurs relationnels

**Spécifique à Microsoft**

Comparez deux objets `_variant_t` pour déterminer leur égalité ou inégalité.

## <a name="syntax"></a>Syntaxe

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
`VARIANT`À comparer à l' `_variant_t` objet.

*pSrc*<br/>
Pointeur vers le `VARIANT` à comparer à l' `_variant_t` objet.

## <a name="return-value"></a>Valeur renvoyée

Retourne **`true`** si la comparaison contient, **`false`** si ce n’est pas le cas.

## <a name="remarks"></a>Notes

Compare un `_variant_t` objet à un `VARIANT` , en testant l’égalité ou l’inégalité.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
