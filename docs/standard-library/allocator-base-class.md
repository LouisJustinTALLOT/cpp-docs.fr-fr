---
title: allocator_base, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: f642c21f2b1060dd5adc5c3d98144592c3413777
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562634"
---
# <a name="allocator_base-class"></a>allocator_base, classe

Définit la classe de base et les fonctions communes nécessaires à la création d’un allocateur défini par l’utilisateur à partir d’un filtre de synchronisation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type des éléments alloués par l'allocateur.

*Synchronisation*\
Stratégie de synchronisation de l’allocateur, qui est la classe [sync_none](sync-none-class.md), [sync_per_container](sync-per-container-class.md), [sync_per_thread](sync-per-thread-class.md) ou [sync_shared](sync-shared-class.md).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[allocator_base](#allocator_base)|Construit un objet de type `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur constant vers le type d'objet géré par l'allocateur.|
|[const_reference](#const_reference)|Type qui fournit une référence constante au type d'objet géré par l'allocateur.|
|[difference_type](#difference_type)|Type intégral signé qui peut représenter la différence entre des valeurs de pointeurs vers le type d'objet géré par l'allocateur.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers le type d'objet géré par l'allocateur.|
|[reference](#reference)|Type qui fournit une référence au type d'objet géré par l'allocateur.|
|[size_type](#size_type)|Type intégral non signé qui peut représenter la longueur d’une séquence qu’un objet de type `allocator_base` peut allouer.|
|[value_type](#value_type)|Type géré par l'allocateur.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[_Charalloc](#charalloc)|Alloue le stockage pour un tableau de type **`char`** .|
|[_Chardealloc](#chardealloc)|Libère le stockage pour le tableau contenant des éléments de type **`char`** .|
|[address](#address)|Recherche l'adresse d'un objet dont la valeur est spécifiée.|
|[lui](#allocate)|Alloue un bloc de mémoire suffisamment grand pour stocker au moins un nombre spécifié d'éléments.|
|[construct](#construct)|Construit un type d'objet spécifique à une adresse spécifiée qui est initialisée avec une valeur spécifiée.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[suppression](#destroy)|Appelle un destructeur d'objets sans libérer la mémoire où l'objet était stocké.|
|[max_size](#max_size)|Retourne le nombre d’éléments de type *Type* qui pourraient être alloués par un objet de classe allocator avant que la mémoire libre soit complètement utilisée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a> allocator_base :: _Charalloc

Alloue le stockage pour un tableau de type **`char`** .

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments du tableau à allouer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée par les conteneurs quand la compilation s’effectue avec un compilateur qui ne peut pas compiler rebind. Il implémente `_Charalloc` pour l’allocateur défini par l’utilisateur en retournant le résultat d’un appel à la fonction `allocate` du filtre de synchronisation.

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a> allocator_base :: _Chardealloc

Libère le stockage pour le tableau contenant des éléments de type **`char`** .

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers le premier objet à désallouer dans le stockage.

*saut*\
Nombre d’objets à désallouer dans le stockage.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée par les conteneurs quand la compilation s’effectue avec un compilateur qui ne peut pas compiler rebind. Il implémente `_Chardealloc` pour l’allocateur défini par l’utilisateur en appelant la fonction `deallocate` du filtre de synchronisation. Le pointeur PTR doit avoir été retourné précédemment par un appel à `_Charalloc` pour un objet allocateur dont la valeur est égale à **`*this`** , en allouant un objet tableau de même taille et de même type. `_Chardealloc` ne lève jamais d’exception.

## <a name="allocator_baseaddress"></a><a name="address"></a> allocator_base :: Address

Recherche l'adresse d'un objet dont la valeur est spécifiée.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Valeur const ou nonconst de l’objet dont l’adresse est recherchée.

### <a name="return-value"></a>Valeur de retour

Pointeur const ou nonconst vers l’objet trouvé d’une valeur const ou nonconst, respectivement.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en retournant `&val`.

## <a name="allocator_baseallocate"></a><a name="allocate"></a> allocator_base :: Allocate

Alloue un bloc de mémoire suffisamment grand pour stocker au moins un nombre spécifié d'éléments.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Paramètres

*_Nx*\
Nombre d’éléments du tableau à allouer.

*_Hint*\
Ce paramètre est ignoré.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

La fonction membre implémente l’allocation de mémoire pour l’allocateur défini par l’utilisateur en retournant le résultat d’un appel à la fonction `allocate` du filtre de synchronisation de type Type `*` si `_Nx == 1`, sinon en retournant le résultat d’un appel au cast de `operator new(_Nx * sizeof(Type))` en type Type `*`.

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a> allocator_base :: allocator_base

Construit un objet de type `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet allocateur à copier.

### <a name="remarks"></a>Notes

Le premier constructeur construit une instance [allocator_base](allocator-base-class.md). Le deuxième constructeur construit une instance `allocator_base` telle que pour toute instance `allocator_base<Type, _Sync>``a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a> allocator_base :: const_pointer

Type qui fournit un pointeur constant vers le type d'objet géré par l'allocateur.

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a> allocator_base :: const_reference

Type qui fournit une référence constante au type d'objet géré par l'allocateur.

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a> allocator_base :: Construct

Construit un type d'objet spécifique à une adresse spécifiée qui est initialisée avec une valeur spécifiée.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers l’emplacement où l’objet doit être construit.

*multiples*\
Valeur avec laquelle l’objet en cours de construction doit être initialisé.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `new((void*)ptr Type(val)`.

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a> allocator_base ::d eallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers le premier objet à désallouer dans le stockage.

*_Nx*\
Nombre d’objets à désallouer dans le stockage.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `deallocate(ptr)` sur le filtre de synchronisation `Sync` si `_Nx == 1`, sinon en appelant `operator delete(_Nx * ptr)`.

## <a name="allocator_basedestroy"></a><a name="destroy"></a> allocator_base ::d estroy

Appelle un destructeur d'objets sans libérer la mémoire où l'objet était stocké.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur désignant l’adresse de l’objet à détruire.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en appelant `ptr->~Type()`.

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a> allocator_base ::d ifference_type

Type intégral signé qui peut représenter la différence entre des valeurs de pointeurs vers le type d'objet géré par l'allocateur.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a> allocator_base :: max_size

Retourne le nombre d'éléments de type `Type` qui pourraient être alloués par un objet d'allocateur de classe avant que la mémoire libre soit complètement utilisée.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments pouvant être alloués.

### <a name="remarks"></a>Notes

Cette fonction membre est implémentée pour l’allocateur défini par l’utilisateur en retournant `(size_t)-1 / sizeof(Type)` si `0 < (size_t)-1 / sizeof(Type)`, sinon `1`.

## <a name="allocator_basepointer"></a><a name="pointer"></a> allocator_base ::p ointer

Type qui fournit un pointeur vers le type d'objet géré par l'allocateur.

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a> allocator_base :: référence

Type qui fournit une référence au type d'objet géré par l'allocateur.

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a> allocator_base :: size_type

Type intégral non signé qui peut représenter la longueur d’une séquence qu’un objet de type `allocator_base` peut allouer.

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a> allocator_base :: value_type

Type géré par l'allocateur.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
