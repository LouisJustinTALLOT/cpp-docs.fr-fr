---
title: allocator_base, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f27cb2bc1a711b77006fa496cc080f546e539ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962452"
---
# <a name="allocatorbase-class"></a>allocator_base, classe

Définit la classe de base et les fonctions communes nécessaires à la création d’un allocateur défini par l’utilisateur à partir d’un filtre de synchronisation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|
|*synchronisation*|Stratégie de synchronisation de l’allocateur, qui est la classe [sync_none](../standard-library/sync-none-class.md), [sync_per_container](../standard-library/sync-per-container-class.md), [sync_per_thread](../standard-library/sync-per-thread-class.md) ou [sync_shared](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[allocator_base](#allocator_base)|Construit un objet de type `allocator_base`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur constant vers le type d'objet géré par l'allocateur.|
|[const_reference](#const_reference)|Type qui fournit une référence constante au type d'objet géré par l'allocateur.|
|[difference_type](#difference_type)|Type intégral signé qui peut représenter la différence entre des valeurs de pointeurs vers le type d'objet géré par l'allocateur.|
|[pointer](#pointer)|Type qui fournit un pointeur vers le type d'objet géré par l'allocateur.|
|[reference](#reference)|Type qui fournit une référence au type d'objet géré par l'allocateur.|
|[size_type](#size_type)|Type intégral non signé qui peut représenter la longueur d'une séquence qu'un objet de classe de modèle `allocator_base` peut allouer.|
|[value_type](#value_type)|Type géré par l'allocateur.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[_Charalloc](#charalloc)|Alloue du stockage pour un tableau de type **char**.|
|[_Chardealloc](#chardealloc)|Libère du stockage pour le tableau contenant les éléments de type **char**.|
|[address](#address)|Recherche l'adresse d'un objet dont la valeur est spécifiée.|
|[allocate](#allocate)|Alloue un bloc de mémoire suffisamment grand pour stocker au moins un nombre spécifié d'éléments.|
|[construct](#construct)|Construit un type d'objet spécifique à une adresse spécifiée qui est initialisée avec une valeur spécifiée.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[destroy](#destroy)|Appelle un destructeur d'objets sans libérer la mémoire où l'objet était stocké.|
|[max_size](#max_size)|Retourne le nombre d’éléments de type *Type* qui pourraient être alloués par un objet de classe allocator avant que la mémoire libre soit complètement utilisée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="charalloc"></a>  allocator_base::_Charalloc

Alloue du stockage pour un tableau de type **char**.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*count*|Nombre d’éléments du tableau à allouer.|

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée par les conteneurs quand la compilation s’effectue avec un compilateur qui ne peut pas compiler rebind. Il implémente `_Charalloc` pour l’allocateur défini par l’utilisateur en retournant le résultat d’un appel à la fonction `allocate` du filtre de synchronisation.

## <a name="chardealloc"></a>  allocator_base::_Chardealloc

Libère du stockage pour le tableau contenant les éléments de type **char**.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers le premier objet à désallouer dans le stockage.|
|*count*|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée par les conteneurs quand la compilation s’effectue avec un compilateur qui ne peut pas compiler rebind. Il implémente `_Chardealloc` pour l’allocateur défini par l’utilisateur en appelant la fonction `deallocate` du filtre de synchronisation. Le pointeur ptr doit avoir été retourné précédemment par un appel à `_Charalloc` pour un objet allocateur dont la valeur est égale à `*this`, en allouant un objet tableau de même taille et de même type. `_Chardealloc` ne lève jamais d’exception.

## <a name="address"></a>  allocator_base::address

Recherche l'adresse d'un objet dont la valeur est spécifiée.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Paramètres

*Val* la valeur const ou nonconst de l’objet dont l’adresse est recherchée.

### <a name="return-value"></a>Valeur de retour

Pointeur const ou nonconst vers l’objet trouvé d’une valeur const ou nonconst, respectivement.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en retournant `&val`.

## <a name="allocate"></a>  allocator_base::allocate

Alloue un bloc de mémoire suffisamment grand pour stocker au moins un nombre spécifié d'éléments.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Nombre d’éléments du tableau à allouer.|
|*_Hint*|Ce paramètre est ignoré.|

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

La fonction membre implémente l’allocation de mémoire pour l’allocateur défini par l’utilisateur en retournant le résultat d’un appel à la fonction `allocate` du filtre de synchronisation de type Type `*` si `_Nx == 1`, sinon en retournant le résultat d’un appel au cast de `operator new(_Nx * sizeof(Type))` en type Type `*`.

## <a name="allocator_base"></a>  allocator_base::allocator_base

Construit un objet de type `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*right*|Objet allocateur à copier.|

### <a name="remarks"></a>Notes

Le premier constructeur construit une instance [allocator_base](../standard-library/allocator-base-class.md). Le deuxième constructeur construit une instance `allocator_base` telle que pour toute instance `allocator_base<Type, _Sync>` `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>  allocator_base::const_pointer

Type qui fournit un pointeur constant vers le type d'objet géré par l'allocateur.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>  allocator_base::const_reference

Type qui fournit une référence constante au type d'objet géré par l'allocateur.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>  allocator_base::construct

Construit un type d'objet spécifique à une adresse spécifiée qui est initialisée avec une valeur spécifiée.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers l’emplacement où l’objet doit être construit.|
|*Val*|Valeur avec laquelle l’objet en cours de construction doit être initialisé.|

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `new((void*)ptr Type(val)`.

## <a name="deallocate"></a>  allocator_base::deallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers le premier objet à désallouer dans le stockage.|
|*_Nx*|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `deallocate(ptr)` sur le filtre de synchronisation `Sync` si `_Nx == 1`, sinon en appelant `operator delete(_Nx * ptr)`.

## <a name="destroy"></a>  allocator_base::destroy

Appelle un destructeur d'objets sans libérer la mémoire où l'objet était stocké.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur désignant l’adresse de l’objet à détruire.|

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `ptr->~Type()`.

## <a name="difference_type"></a>  allocator_base::difference_type

Type intégral signé qui peut représenter la différence entre des valeurs de pointeurs vers le type d'objet géré par l'allocateur.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>  allocator_base::max_size

Retourne le nombre d'éléments de type `Type` qui pourraient être alloués par un objet d'allocateur de classe avant que la mémoire libre soit complètement utilisée.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments pouvant être alloués.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en retournant `(size_t)-1 / sizeof(Type)` si `0 < (size_t)-1 / sizeof(Type)`, sinon `1`.

## <a name="pointer"></a>  allocator_base::pointer

Type qui fournit un pointeur vers le type d'objet géré par l'allocateur.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>  allocator_base::reference

Type qui fournit une référence au type d'objet géré par l'allocateur.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>  allocator_base::size_type

Type intégral non signé qui peut représenter la longueur d'une séquence qu'un objet de classe de modèle `allocator_base` peut allouer.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>  allocator_base::value_type

Type géré par l'allocateur.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
