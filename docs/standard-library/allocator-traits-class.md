---
title: allocator_traits, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: c9c03eb688a71e0587ca4faa14d89d8487d4ec59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617413"
---
# <a name="allocator_traits-class"></a>allocator_traits, classe

Le modèle de classe décrit un objet qui complète un *type d’allocateur*. Un type d’allocateur est tout type qui décrit un objet allocateur utilisé pour la gestion de stockage alloué. Plus précisément, pour tout type d’allocateur `Alloc`, vous pouvez utiliser `allocator_traits<Alloc>` afin de déterminer toutes les informations nécessaires pour un conteneur compatible avec l’allocateur. Pour plus d’informations, consultez [allocator, classe](allocator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`allocator_type`|Le type est un synonyme du paramètre de modèle `Alloc`.|
|`const_pointer`|Ce type est `Alloc::const_pointer` s’il est correctement construit ; sinon, `pointer_traits<pointer>::rebind<const value_type>`.|
|`const_void_pointer`|Ce type est `Alloc::const_void_pointer` s’il est correctement construit ; sinon, `pointer_traits<pointer>::rebind<const void>`.|
|`difference_type`|Ce type est `Alloc::difference_type` s’il est correctement construit ; sinon, `pointer_traits<pointer>::difference_type`.|
|`pointer`|Ce type est `Alloc::pointer` s’il est correctement construit ; sinon, `value_type *`.|
|`propagate_on_container_copy_assignment`|Ce type est `Alloc::propagate_on_container_copy_assignment` s’il est correctement construit ; sinon, `false_type`.|
|`propagate_on_container_move_assignment`|Ce type est `Alloc::propagate_on_container_move_assignment` s’il est correctement construit ; sinon, `false_type`. Si le type donne la valeur true, un conteneur compatible avec l’allocateur copie son allocateur stocké sur une assignation de déplacement.|
|`propagate_on_container_swap`|Ce type est `Alloc::propagate_on_container_swap` s’il est correctement construit ; sinon, `false_type`. Si le type donne la valeur true, un conteneur compatible avec l’allocateur échange son allocateur stocké sur un échange.|
|`size_type`|Ce type est `Alloc::size_type` s’il est correctement construit ; sinon, `make_unsigned<difference_type>::type`.|
|`value_type`|Ce type est un synonyme de `Alloc::value_type`.|
|`void_pointer`|Ce type est `Alloc::void_pointer` s’il est correctement construit ; sinon, `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Méthodes statiques

Les méthodes statiques suivantes appellent la méthode correspondante sur un paramètre d’allocateur donné.

|||
|-|-|
|[allocate](#allocate)|Méthode statique qui alloue de la mémoire en utilisant le paramètre d’allocateur donné.|
|[construct](#construct)|Méthode statique qui utilise un allocateur spécifié pour construire un objet.|
|[libérer](#deallocate)|Méthode statique qui utilise un allocateur spécifié pour désallouer un nombre spécifié d’objets.|
|[suppression](#destroy)|Méthode statique qui utilise un allocateur spécifié pour appeler le destructeur sur un objet sans désallouer sa mémoire.|
|[max_size](#max_size)|Méthode statique qui utilise un allocateur spécifié pour déterminer le nombre maximal d’objets pouvant être alloués.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Méthode statique qui appelle `select_on_container_copy_construction` sur l’allocateur spécifié.|

### <a name="allocate"></a><a name="allocate"></a>lui

Méthode statique qui alloue de la mémoire en utilisant le paramètre d’allocateur donné.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

*saut*\
Nombre d’éléments à allouer.

*évit*\
`const_pointer` pouvant aider l’objet allocateur à satisfaire la demande de stockage en recherchant l’adresse d’un objet alloué avant la demande. Un pointeur null est traité comme s’il n’y avait aucun argument hint.

#### <a name="return-value"></a>Valeur renvoyée

Chaque méthode retourne un pointeur vers l’objet alloué.

La première méthode statique retourne `al.allocate(count)`.

La seconde méthode retourne `al.allocate(count, hint)`, si cette expression est correctement construite ; sinon, `al.allocate(count)`.

### <a name="construct"></a><a name="construct"></a>composer

Méthode statique qui utilise un allocateur spécifié pour construire un objet.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

*effectués*\
Pointeur vers l’emplacement où l’objet doit être construit.

*attend*\
Liste d’arguments passée au constructeur d’objet.

#### <a name="remarks"></a>Notes

La fonction membre statique appelle `al.construct(ptr, args...)`, si cette expression est correctement construite ; sinon, elle retourne la valeur `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

### <a name="deallocate"></a><a name="deallocate"></a>libérer

Méthode statique qui utilise un allocateur spécifié pour désallouer un nombre spécifié d’objets.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

*effectués*\
Pointeur vers l’emplacement de départ des objets à désallouer.

*saut*\
Nombre d’objets à désallouer.

#### <a name="remarks"></a>Notes

Cette méthode appelle `al.deallocate(ptr, count)`.

Cette méthode ne lève aucune exception.

### <a name="destroy"></a><a name="destroy"></a>suppression

Méthode statique qui utilise un allocateur spécifié pour appeler le destructeur sur un objet sans désallouer sa mémoire.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

*effectués*\
Pointeur vers l’emplacement de l’objet.

#### <a name="remarks"></a>Notes

Cette méthode appelle `al.destroy(ptr)`, si cette expression est correctement construite ; sinon, elle retourne la valeur `ptr->~Uty()`.

### <a name="max_size"></a><a name="max_size"></a>max_size

Méthode statique qui utilise un allocateur spécifié pour déterminer le nombre maximal d’objets pouvant être alloués.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

#### <a name="remarks"></a>Notes

Cette méthode retourne `al.max_size()`, si cette expression est correctement construite ; sinon, `numeric_limits<size_type>::max()`.

### <a name="select_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>select_on_container_copy_construction

Méthode statique qui appelle `select_on_container_copy_construction` sur l’allocateur spécifié.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>Paramètres

*&*\
Objet allocateur.

#### <a name="return-value"></a>Valeur renvoyée

Cette méthode retourne `al.select_on_container_copy_construction()` si ce type est correctement construit ; sinon, elle retourne *al*.

#### <a name="remarks"></a>Notes

Cette méthode est utilisée pour spécifier un allocateur quand le conteneur associé est construit par copie.
