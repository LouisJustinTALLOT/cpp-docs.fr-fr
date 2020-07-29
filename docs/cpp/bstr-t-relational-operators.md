---
title: Opérateurs relationnels _bstr_t
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: 8fc163255a5ab342938f56f8a22af3984a48e56a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216620"
---
# <a name="_bstr_t-relational-operators"></a>Opérateurs relationnels _bstr_t

**Spécifique à Microsoft**

Compare deux objets `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>Notes

Ces opérateurs comparent deux objets `_bstr_t` du point de vue lexicographique. Les opérateurs retournent **`true`** si les comparaisons sont conservées, sinon retourne **`false`** .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
