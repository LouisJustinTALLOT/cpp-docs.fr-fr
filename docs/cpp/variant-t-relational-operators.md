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
ms.openlocfilehash: 6e0296a2bf4ce97e41fdf6208c3dd1c6b91215dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226936"
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

## <a name="return-value"></a>Valeur de retour

Retourne **`true`** si la comparaison contient, **`false`** si ce n’est pas le cas.

## <a name="remarks"></a>Notes

Compare un `_variant_t` objet à un `VARIANT` , en testant l’égalité ou l’inégalité.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
