---
title: '&lt;scoped_allocator&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 7c9f2c3a2425bf3ac6e62ce7fcecfe9315c3e04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348196"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt;, opérateurs

|||
|-|-|
|[!=, opérateur](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

Teste si deux objets `scoped_allocator_adaptor` sont inégaux.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet gauche `scoped_allocator_adaptor`.

*right*<br/>
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur de retour

`!(left == right)`

## <a name="op_eq_eq"></a>  operator==

Teste si deux objets `scoped_allocator_adaptor` sont égaux.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Objet gauche `scoped_allocator_adaptor`.

*right*<br/>
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur de retour

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Voir aussi

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
