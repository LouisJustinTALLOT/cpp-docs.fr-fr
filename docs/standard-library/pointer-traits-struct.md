---
title: pointer_traits, struct
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
ms.openlocfilehash: 1ed8d61a52c11ab48fe6f762ff342ea88d107b14
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832696"
---
# <a name="pointer_traits-struct"></a>pointer_traits, struct

Fournit les informations nécessaires à un objet de type `allocator_traits` pour décrire un allocateur avec le type pointeur `Ptr` .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>Notes

Le pointeur Ptr peut être un pointeur brut du type `Ty *` ou une classe ayant les propriétés suivantes.

```cpp
struct Ptr
{ // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj); // optional
};
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|`typedef T2 difference_type`|Le type `T2` est `Ptr::difference_type` si ce type existe. Sinon, le type est `ptrdiff_t`. Si `Ptr` est un pointeur brut, le type est `ptrdiff_t`.|
|`typedef T1 element_type`|Le type `T1` est `Ptr::element_type` si ce type existe. Sinon, le type est `Ty`. Si `Ptr` est un pointeur brut, le type est `Ty`.|
|`typedef Ptr pointer`|Le type est `Ptr`.|

### <a name="structs"></a>Structures

|Nom|Description|
|-|-|
|`rebind`|Tente de convertir le type de pointeur sous-jacent en un type spécifié.|

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[pointer_to](#pointer_to)|Convertit une référence arbitraire à un objet de la classe `Ptr`.|

### <a name="pointer_to"></a><a name="pointer_to"></a> pointer_to

Méthode statique qui retourne `Ptr::pointer_to(obj)`, si cette fonction existe. Sinon, il n’est pas possible de convertir une référence arbitraire à un objet de la classe `Ptr`. Si `Ptr` est un pointeur brut, cette méthode retourne `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
