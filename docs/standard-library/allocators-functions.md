---
title: '&lt;allocators&gt;, macros'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: dbf7577969ec43de47339bf80327007ac857a5a7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834971"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt;, macros

:::row:::
   :::column span="":::
      [`ALLOCATOR_DECL`](#allocator_decl)\
      [`CACHE_CHUNKLIST`](#cache_chunklist)
   :::column-end:::
   :::column span="":::
      [`CACHE_FREELIST`](#cache_freelist)
   :::column-end:::
   :::column span="":::
      [`CACHE_SUBALLOC`](#cache_suballoc)
   :::column-end:::
   :::column span="":::
      [`SYNC_DEFAULT`](#sync_default)
   :::column-end:::
:::row-end:::

## <a name="allocator_decl"></a><a name="allocator_decl"></a> ALLOCATOR_DECL

Produit un modèle de classe Allocator.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Notes

La macro génère une définition de modèle `template <class Type> class name {.....}` et une spécialisation `template <> class name<void> {.....}` qui définissent ensemble un modèle de classe Allocator qui utilise le filtre `sync` de synchronisation et un cache de type `cache` .

Pour les compilateurs qui peuvent compiler rebind, la définition de modèle obtenue ressemble à ceci :

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Pour les compilateurs qui ne peuvent pas compiler rebind, la définition de modèle obtenue ressemble à ceci :

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a> CACHE_CHUNKLIST

Génère `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Notes

## <a name="cache_freelist"></a><a name="cache_freelist"></a> CACHE_FREELIST

Génère `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Notes

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a> CACHE_SUBALLOC

Génère `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Notes

## <a name="sync_default"></a><a name="sync_default"></a> SYNC_DEFAULT

Génère un filtre de synchronisation.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Notes

Si un compilateur prend en charge la compilation d’applications monothread et multithread, pour les applications monothread, la macro génère `stdext::allocators::sync_none` ; dans tous les autres cas, elle génère `stdext::allocators::sync_shared`.

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
