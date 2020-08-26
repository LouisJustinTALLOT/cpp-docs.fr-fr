---
title: '&lt;scoped_allocator&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 907772069c192b3ef75c7366e079b1da1dd36f8d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846249"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt;, opérateurs

[opérateur ! =](#op_neq)\
[opérateur = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si deux objets `scoped_allocator_adaptor` sont inégaux.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet gauche `scoped_allocator_adaptor`.

*Oui*\
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur renvoyée

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si deux objets `scoped_allocator_adaptor` sont égaux.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet gauche `scoped_allocator_adaptor`.

*Oui*\
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur renvoyée

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Voir aussi

[<scoped_allocator>](../standard-library/scoped-allocator.md)
