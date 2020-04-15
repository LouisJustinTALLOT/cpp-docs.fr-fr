---
title: '&lt;scoped_allocator&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 45da89793c3f4ea131404fc3392413e7aea9ef3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373383"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt;, opérateurs

|||
|-|-|
|[opérateur!](#op_neq)|[opérateur](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>opérateur!

Teste si deux objets `scoped_allocator_adaptor` sont inégaux.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `scoped_allocator_adaptor`.

*Oui*\
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur de retour

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur

Teste si deux objets `scoped_allocator_adaptor` sont égaux.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `scoped_allocator_adaptor`.

*Oui*\
Objet droit `scoped_allocator_adaptor`.

### <a name="return-value"></a>Valeur de retour

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Voir aussi

[>scoped_allocator<](../standard-library/scoped-allocator.md)
