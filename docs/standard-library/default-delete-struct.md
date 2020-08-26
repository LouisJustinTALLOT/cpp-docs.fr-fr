---
title: Struct default_delete
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: 8baa9f5d294cf083fd55414cd529e438f328d1a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845079"
---
# <a name="default_delete-struct"></a>Struct default_delete

Objet de fonction prédéfini qui effectue l’opération de division ( `operator/` ) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Configuration requise

**En-tête :**\<memory>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[default_delete](#default_delete)|Constructeur des objets de type `default_delete`.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[, opérateur ()](#op_paren)|Opérateur de référence auquel accéder `default_delete` .|

## <a name="default_delete"></a><a name="default_delete"></a> default_delete

Constructeur des objets de type `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="operator"></a><a name="op_paren"></a> , opérateur ()

Opérateur de référence auquel accéder `default_delete` .

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Voir aussi

[\<memory>](../standard-library/memory.md)
