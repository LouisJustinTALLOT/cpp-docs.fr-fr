---
title: default_delete Struct
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269261"
---
# <a name="defaultdelete-struct"></a>default_delete Struct

Un objet de fonction prédéfini qui effectue l’opération de division (`operator/`) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[default_delete](#default_delete)|Constructeur des objets de type `default_delete`.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator()](#op_paren)|Un opérateur de référence pour accéder à `default_delete`.|

## <a name="default_delete"></a> default_delete

Constructeur des objets de type `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> operator()

Un opérateur de référence pour accéder à `default_delete`.

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Voir aussi

[\<memory>](../standard-library/memory.md)
