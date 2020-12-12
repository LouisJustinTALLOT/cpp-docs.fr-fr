---
description: 'En savoir plus sur les opérateurs suivants : &lt; scoped_allocator &gt;'
title: '&lt;scoped_allocator&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 2f32a42ded9c73cbc2608f3e39f3566deee20e83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197137"
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
