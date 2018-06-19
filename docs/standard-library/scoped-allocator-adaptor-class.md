---
title: scoped_allocator_adaptor, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
dev_langs:
- C++
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e403e0133818846deb08bb336adc98618e944bf9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861875"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor::construct, classe

Représente une imbrication d’allocateurs.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Notes

La classe de modèle encapsule une imbrication d’un ou de plusieurs allocateurs. Cette classe a un allocateur externe de type `outer_allocator_type`, un synonyme de `Outer`, qui est une base publique de l’objet `scoped_allocator_adaptor`. `Outer` s’utilise pour allouer de la mémoire pour un conteneur. Vous pouvez obtenir une référence à cet objet de base allocateur en appelant `outer_allocator`.

Le reste de l’imbrication a le type `inner_allocator_type`. Un allocateur interne s’utilise pour allouer de la mémoire pour les éléments dans un conteneur. Vous pouvez obtenir une référence à l’objet stocké de ce type en appelant `inner_allocator`. Si `Inner...` n’est pas vide, `inner_allocator_type` a le type `scoped_allocator_adaptor<Inner...>`, et `inner_allocator` désigne un objet membre. Sinon, `inner_allocator_type` a le type `scoped_allocator_adaptor<Outer>`, et `inner_allocator` désigne l’objet entier.

L’imbrication se comporte comme si elle avait une profondeur arbitraire, en répliquant son allocateur encapsulé le plus profond selon les besoins.

Plusieurs concepts qui ne font pas partie de l’interface visible aident à décrire le comportement de cette classe de modèle. Un *allocateur externe* sert d’intermédiaire pour tous les appels aux méthodes construct et destroy. Il est défini par la fonction récursive `OUTERMOST(X)`, où `OUTERMOST(X)` est l’une des valeurs suivantes.

- Si `X.outer_allocator()` est bien formé, `OUTERMOST(X)` est `OUTERMOST(X.outer_allocator())`.

- Sinon, `OUTERMOST(X)` est `X`.

Trois types sont définis pour les besoins de la démonstration :

|Type|Description|
|----------|-----------------|
|`Outermost`|Type d'élément `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Constructeurs

|Name|Description|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Construit un objet `scoped_allocator_adaptor`.|

### <a name="typedefs"></a>Typedef

|Nom|Description|
|----------|-----------------|
|`const_pointer`|Ce type est un synonyme du `const_pointer` qui est associé à l’allocateur `Outer`.|
|`const_void_pointer`|Ce type est un synonyme du `const_void_pointer` qui est associé à l’allocateur `Outer`.|
|`difference_type`|Ce type est un synonyme du `difference_type` qui est associé à l’allocateur `Outer`.|
|`inner_allocator_type`|Ce type est un synonyme du type de l’adaptateur imbriqué `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Ce type est un synonyme du type de l’adaptateur de base `Outer`.|
|`pointer`|Ce type est un synonyme du `pointer` qui est associé à l’allocateur `Outer`.|
|`propagate_on_container_copy_assignment`|Le type a la valeur true uniquement si `Outer_traits::propagate_on_container_copy_assignment` ou `inner_allocator_type::propagate_on_container_copy_assignment` a la valeur true.|
|`propagate_on_container_move_assignment`|Le type a la valeur true uniquement si `Outer_traits::propagate_on_container_move_assignment` ou `inner_allocator_type::propagate_on_container_move_assignment` a la valeur true.|
|`propagate_on_container_swap`|Le type a la valeur true uniquement si `Outer_traits::propagate_on_container_swap` ou `inner_allocator_type::propagate_on_container_swap` a la valeur true.|
|`size_type`|Ce type est un synonyme du `size_type` qui est associé à l’allocateur `Outer`.|
|`value_type`|Ce type est un synonyme du `value_type` qui est associé à l’allocateur `Outer`.|
|`void_pointer`|Ce type est un synonyme du `void_pointer` qui est associé à l’allocateur `Outer`.|

### <a name="structs"></a>Structs

|Name|Description|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind, struct](#rebind_struct)|Définit le type `Outer::rebind\<Other>::other` comme synonyme de `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[allocate](#allocate)|Alloue de la mémoire à l’aide de l’allocateur `Outer`.|
|[construct](#construct)|Construit un objet.|
|[deallocate](#deallocate)|Libère des objets à l’aide de l’allocateur externe.|
|[destroy](#destroy)|Détruit un objet spécifié.|
|[inner_allocator](#inner_allocator)|Récupère une référence à l’objet stocké de type `inner_allocator_type`.|
|[max_size](#max_size)|Détermine le nombre maximal d’objets pouvant être alloués par l’allocateur externe.|
|[outer_allocator](#outer_allocator)|Récupère une référence à l’objet stocké de type `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Crée un objet `scoped_allocator_adaptor` où chaque objet allocateur stocké est initialisé en appelant `select_on_container_copy_construction` pour chaque allocateur correspondant.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<scoped_allocator>

**Espace de noms :** std

## <a name="allocate"></a>  scoped_allocator_adaptor::Allocate

Alloue de la mémoire à l’aide de l’allocateur `Outer`.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Paramètres

`count` Le nombre d’éléments pour lesquels suffisamment de stockage doit être alloué.

`hint` Un pointeur qui peut aider à l’objet allocateur en recherchant l’adresse d’un objet alloué avant la demande.

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne `Outer_traits::allocate(outer_allocator(), count)`. La deuxième fonction membre retourne `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="construct"></a>  scoped_allocator_adaptor::Construct

Construit un objet.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Paramètres

`ptr` Pointeur vers l’emplacement de mémoire où l’objet doit être construite.

`args` Une liste d’arguments.

`first` Un objet du premier type d’une paire.

`second` Un objet du second type d’une paire.

`right` Un objet existant à être déplacée ou copiée.

### <a name="remarks"></a>Notes

La première méthode construit l’objet à l’emplacement `ptr` en appelant `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, où `xargs...` est l’une des valeurs suivantes.

- Si `uses_allocator<Ty, inner_allocator_type>` a la valeur false, `xargs...` est `args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` et `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` ont la valeur true, `xargs...` est `allocator_arg, inner_allocator(), args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` et `is_constructible<Ty, args..., inner_allocator()>` ont la valeur true, `xargs...` est `args..., inner_allocator()`.

La deuxième méthode construit la paire à l’emplacement `ptr` en appelant `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, où `xargs...` est `first...` modifié comme dans la liste ci-dessus, et en appelant `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, où `xargs...` est `second...` modifié comme dans la liste ci-dessus.

La troisième méthode se comporte comme `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

La quatrième méthode se comporte comme `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

La cinquième méthode se comporte comme `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

La sixième méthode se comporte comme `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>  scoped_allocator_adaptor::deallocate

Libère des objets à l’aide de l’allocateur externe.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Paramètres

`ptr` Pointeur vers l’emplacement de départ de l’objet à être libéré.

`count` Le nombre d’objets à libérer.

## <a name="destroy"></a>  scoped_allocator_adaptor::destroy

Détruit un objet spécifié.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Paramètres

`ptr` Pointeur vers l’objet point d’être détruit.

### <a name="return-value"></a>Valeur de retour

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator

Récupère une référence à l’objet stocké de type `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet stocké de type `inner_allocator_type`.

## <a name="max_size"></a>  scoped_allocator_adaptor::max_size

Détermine le nombre maximal d’objets pouvant être alloués par l’allocateur externe.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Valeur de retour

`Outer_traits::max_size(outer_allocator())`

## <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator

Récupère une référence à l’objet stocké de type `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet stocké de type `outer_allocator_type`.

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind, struct

Définit le type `Outer::rebind\<Other>::other` comme synonyme de `scoped_allocator_adaptor\<Other, Inner...>`.

la reliaison struct {typedef Other_traits::rebind\<autres > Other_alloc ; typedef scoped_allocator_adaptor\<Other_alloc, interne... > autres ;} ;

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor, constructeur

Construit un objet `scoped_allocator_adaptor`.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;
```

### <a name="parameters"></a>Paramètres

`right` Existant `scoped_allocator_adaptor`.

`al` Un allocateur existant à utiliser comme l’allocateur externe.

`rest` Liste des allocateurs à utiliser en tant que les allocateurs internes.

### <a name="remarks"></a>Notes

Le premier constructeur construit par défaut ses objets allocateur stockés. Chacun des trois constructeurs suivants construit ses objets allocateur stockés à partir des objets correspondants dans `right`. Le dernier constructeur construit ses objets allocateur stockés à partir des arguments correspondants dans la liste d’arguments.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction

Crée un objet `scoped_allocator_adaptor` où chaque objet allocateur stocké est initialisé en appelant `select_on_container_copy_construction` pour chaque allocateur correspondant.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Le résultat est un nouvel objet `scoped_allocator_adaptor` où chaque objet allocateur stocké est initialisé en appelant `al.select_on_container_copy_construction()` pour l’allocateur correspondant `al`.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
