---
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
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187568"
---
# <a name="_variant_t-relational-operators"></a>_variant_t, opérateurs relationnels

**Section spécifique de Microsoft**

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
`VARIANT` à comparer à l’objet `_variant_t`.

*pSrc*<br/>
Pointeur vers le `VARIANT` à comparer avec l’objet `_variant_t`.

## <a name="return-value"></a>Valeur de retour

Retourne la **valeur true** si la comparaison contient, **false** dans le cas contraire.

## <a name="remarks"></a>Notes

Compare un objet `_variant_t` à un `VARIANT`, en testant l’égalité ou l’inégalité.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
