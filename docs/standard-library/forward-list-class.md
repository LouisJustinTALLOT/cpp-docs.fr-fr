---
description: 'En savoir plus sur : classe forward_list'
title: forward_list, classe
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: 3d9cb038123b093f81f5eb4fca49db77885ff1d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232406"
---
# <a name="forward_list-class"></a>forward_list, classe

Décrit un objet qui contrôle une séquence de longueur variable constituée d'éléments. La séquence est stockée en tant que liste de nœuds à liaison unique, chacun contenant un membre de type `Type`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Paramètres

Tapez * \
Type de données d'élément à stocker dans le forward_list.

*Allocateur*\
Objet allocateur stocké qui contient des informations sur l'allocation et la désallocation de mémoire du forward_list. Ce paramètre est facultatif. La valeur par défaut est Allocator<`Type`>.

## <a name="remarks"></a>Notes

Un `forward_list` objet alloue et libère du stockage pour la séquence qu’il contrôle via un objet stocké de Class *Allocator* basé sur la [classe Allocator](../standard-library/allocator-class.md) (communément appelée `std::allocator)` . Pour plus d’informations, consultez [allocators](../standard-library/allocators.md). Un objet allocateur doit avoir la même interface externe qu’un objet de type `allocator` .

> [!NOTE]
> L'objet allocateur stocké n'est pas copié quand l'objet conteneur est assigné.

Les itérateurs, pointeurs et références peuvent devenir non valides quand des éléments de leur séquence contrôlée sont effacés via `forward_list`. Les insertions et jointures effectuées sur la séquence contrôlée via `forward_list` n'invalident pas les itérateurs.

Des ajouts à la séquence contrôlée peuvent être effectués par des appels à [forward_list::insert_after](#insert_after), qui est la seule fonction membre qui appelle le constructeur `Type(const  T&)`. `forward_list` peut également appeler des constructeurs de déplacement. Si une telle expression lève une exception, l'objet conteneur n'insère aucun nouvel élément et relève l'exception. Ainsi, un objet de type `forward_list` est laissé dans un état connu lorsque de telles exceptions se produisent.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[forward_list](#forward_list)|Construit un objet de type `forward_list`.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[allocator_type](#allocator_type)|Type qui représente la classe d'allocateur pour un forward_list.|
|[const_iterator](#const_iterator)|Type qui fournit un itérateur constant pour le forward_list.|
|[const_pointer](#const_pointer)|Type qui fournit un pointeur vers un **`const`** élément dans une liste Forward.|
|[const_reference](#const_reference)|Type qui fournit une référence constante à un élément dans le forward_list.|
|[difference_type](#difference_type)|Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un forward_list au sein d'une plage, parmi les éléments vers lesquels pointent les itérateurs.|
|[répétiteur](#iterator)|Type qui fournit un itérateur pour le forward_list.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément du forward_list.|
|[reference](#reference)|Type qui fournit une référence à un élément du forward_list.|
|[size_type](#size_type)|Type qui représente la distance non signée entre deux éléments.|
|[value_type](#value_type)|Type qui représente le type d'élément stocké dans un forward_list.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[assign](#assign)|Efface les éléments d'un forward_list et copie un nouvel ensemble d'éléments dans un forward_list cible.|
|[before_begin](#before_begin)|Retourne un itérateur qui traite la position avant le premier élément dans un forward_list.|
|[commencer](#begin)|Retourne un itérateur qui traite le premier élément d'un forward_list.|
|[cbefore_begin](#cbefore_begin)|Retourne un itérateur const qui traite la position avant le premier élément dans un forward_list.|
|[cbegin](#cbegin)|Retourne un itérateur const qui traite le premier élément d'un forward_list.|
|[cend](#cend)|Retourne un itérateur const qui traite l'emplacement suivant le dernier élément d'un forward_list.|
|[clear](#clear)|Efface tous les éléments d'un forward_list.|
|[emplace_after](#emplace_after)|Construit par déplacement un nouvel élément après la position spécifiée.|
|[emplace_front](#emplace_front)|Ajoute un élément construit sur place au début de la liste.|
|[empty](#empty)|Teste si un forward_list est vide.|
|[end](#end)|Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un forward_list.|
|[erase_after](#erase_after)|Supprime les éléments du forward_list après une position spécifiée.|
|[frontal](#front)|Retourne une référence au premier élément d'un forward_list.|
|[get_allocator](#get_allocator)|Retourne une copie de l'objet allocateur utilisé pour construire un forward_list.|
|[insert_after](#insert_after)|Ajoute des éléments au forward_list après une position spécifiée.|
|[max_size](#max_size)|Retourne la longueur maximale d'un forward_list.|
|[fusion](#merge)|Supprime les éléments de la liste d'arguments, les insère dans le forward_list cible, puis classe le nouvel ensemble combiné d'éléments dans l'ordre croissant ou dans un autre ordre spécifique.|
|[pop_front](#pop_front)|Supprime l'élément au début d'un forward_list.|
|[push_front](#push_front)|Ajoute un élément au début d'un forward_list.|
|[remove](#remove)|Efface les éléments dans un forward_list qui correspond à une valeur spécifiée.|
|[remove_if](#remove_if)|Efface les éléments d’un forward_list pour lequel un prédicat spécifié est satisfait.|
|[redimensionner](#resize)|Spécifie une nouvelle taille pour un forward_list.|
|[reverse](#reverse)|Inverse l'ordre dans lequel les éléments apparaissent dans un forward_list.|
|[sort](#sort)|Réorganise les éléments dans l’ordre croissant ou dans un ordre spécifié par un prédicat.|
|[splice_after](#splice_after)|Réassocie les liens entre les nœuds.|
|[swap](#swap)|Échange les éléments de deux forward_list.|
|[unique](#unique)|Supprime des éléments adjacents qui réussissent un test spécifié.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace les éléments du forward_list par une copie d'un autre forward_list.|

## <a name="allocator_type"></a><a name="allocator_type"></a> allocator_type

Type qui représente la classe d'allocateur pour un forward_list.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Notes

`allocator_type` est un synonyme du paramètre de modèle Allocator.

## <a name="assign"></a><a name="assign"></a> assignés

Efface les éléments d'un forward_list et copie un nouvel ensemble d'éléments dans un forward_list cible.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Paramètres

*premier*\
Début de la plage de remplacement.

*famille*\
Fin de la plage de remplacement.

*saut*\
Nombre d’éléments à assigner.

*multiples*\
Valeur à assigner à chaque élément.

*Entrer*\
Type de la valeur.

*IList*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Si forward_list est de type entier, la première fonction membre se comporte comme `assign((size_type)First, (Type)Last)`. Dans le cas contraire, la première fonction membre remplace la séquence contrôlée par par **`*this`** la séquence [ `First, Last)` , qui ne doit pas chevaucher la séquence contrôlée initiale.

La deuxième fonction membre remplace la séquence contrôlée par par **`*this`** une répétition d' `Count` éléments de valeur `Val` .

La troisième fonction membre copie les éléments d’initializer_list dans forward_list.

## <a name="before_begin"></a><a name="before_begin"></a> before_begin

Retourne un itérateur qui traite la position avant le premier élément dans un forward_list.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’avant qui pointe juste avant le premier élément de la séquence (ou juste avant la fin d’une séquence vide).

### <a name="remarks"></a>Notes

## <a name="begin"></a><a name="begin"></a> commencer

Retourne un itérateur qui traite le premier élément d'un forward_list.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’avant qui pointe sur le premier élément de la séquence (ou juste après la fin d’une séquence vide).

### <a name="remarks"></a>Notes

## <a name="cbefore_begin"></a><a name="cbefore_begin"></a> cbefore_begin

Retourne un itérateur const qui traite la position avant le premier élément dans un forward_list.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur vers l’avant qui pointe juste avant le premier élément de la séquence (ou juste avant la fin d’une séquence vide).

### <a name="remarks"></a>Notes

## <a name="cbegin"></a><a name="cbegin"></a> cbegin

Retourne un **`const`** itérateur qui traite le premier élément de la plage.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`const`** Itérateur d’accès en avant qui pointe vers le premier élément de la plage, ou vers l’emplacement situé juste après la fin d’une plage vide (pour une plage vide, `cbegin() == cend()` ).

### <a name="remarks"></a>Notes

Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `begin()` et `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> CEND

Retourne un **`const`** itérateur qui traite l’emplacement juste après le dernier élément d’une plage.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur d'accès direct qui pointe juste après la fin de la plage.

### <a name="remarks"></a>Notes

`cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.

Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans l’exemple, considérez qu' `Container` il s’agit d’un conteneur modifiable (autre **`const`** que) de tout type qui prend en charge `end()` et `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

La valeur retournée par `cend` ne doit pas être déréférencée.

## <a name="clear"></a><a name="clear"></a> effacé

Efface tous les éléments d'un forward_list.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

Cette fonction membre appelle `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a><a name="const_iterator"></a> const_iterator

Type qui fournit un itérateur constant pour le forward_list.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Notes

`const_iterator` décrit un objet pouvant servir d’itérateur vers l’avant constant pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l’implémentation.

## <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

Type qui fournit un pointeur vers un **`const`** élément dans une liste Forward.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Notes

## <a name="const_reference"></a><a name="const_reference"></a> const_reference

Type qui fournit une référence constante à un élément dans le forward_list.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Notes

## <a name="difference_type"></a><a name="difference_type"></a> difference_type

Type entier signé qui peut être utilisé pour représenter le nombre d'éléments d'un forward_list au sein d'une plage, parmi les éléments vers lesquels pointent les itérateurs.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Notes

`difference_type` décrit un objet pouvant représenter la différence entre les adresses de deux éléments de la séquence contrôlée.

## <a name="emplace_after"></a><a name="emplace_after"></a> emplace_after

Construit par déplacement un nouvel élément après la position spécifiée.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position dans la liste forward_list cible où le nouvel élément est construit.

*multiples*\
Argument du constructeur.

### <a name="return-value"></a>Valeur renvoyée

Itérateur désignant le nouvel élément inséré.

### <a name="remarks"></a>Notes

Cette fonction membre insère un élément avec les arguments de constructeur *Val* juste après l’élément désigné par *Where* dans la séquence contrôlée. Sinon, son comportement est identique à celui de [forward_list::insert_after](#insert_after).

## <a name="emplace_front"></a><a name="emplace_front"></a> emplace_front

Ajoute un élément construit sur place au début de la liste.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté au début de la liste forward_list.

### <a name="remarks"></a>Notes

Cette fonction membre insère un élément avec les arguments de constructeur `_ val` à la fin de la séquence contrôlée.

Si une exception est levée, le conteneur n’est pas modifié et l’exception est levée de nouveau.

## <a name="empty"></a><a name="empty"></a> vidé

Teste si un forward_list est vide.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste de transfert est vide ; Sinon, **`false`** .

## <a name="end"></a><a name="end"></a> effet

Retourne un itérateur qui traite l'emplacement suivant le dernier élément d'un forward_list.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un itérateur vers l’avant qui pointe juste après la fin de la séquence.

## <a name="erase_after"></a><a name="erase_after"></a> erase_after

Supprime les éléments du forward_list après une position spécifiée.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position dans la liste forward_list cible où le nouvel élément est effacé.

*premier*\
Début de la plage à effacer.

*famille*\
Fin de la plage à effacer.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [forward_list::end](#end) si aucun élément de ce genre n’existe.

### <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée juste après *où*.

La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage `( first,  last)` (aucun point de fin n’est inclus).

L’effacement de `N` éléments entraîne `N` appels de destructeur. Une [réallocation](../standard-library/forward-list-class.md) se produit, et les itérateurs et les références deviennent non valides pour les éléments effacés.

Les fonctions membres ne lèvent jamais d'exception.

## <a name="forward_list"></a><a name="forward_list"></a> forward_list

Construit un objet de type `forward_list`.

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Paramètres

*&*\
Classe allocator à utiliser avec cet objet.

*Saut*\
Nombre d'éléments dans la liste construite.

*Multiples*\
Valeur des éléments contenus dans la liste construite.

*Oui*\
Liste dont la liste construite doit être une copie.

*Premier*\
Position du premier élément de la plage d'éléments à copier.

*Famille*\
Position du premier élément au-delà de la plage d'éléments à copier.

*IList*\
Initializer_list à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un [allocator](../standard-library/allocator-class.md) et initialisent la séquence contrôlée. L’objet Allocator est l’argument *al*, s’il est présent. Pour le constructeur de copie, il s’agit de `right.get_allocator()`. Sinon, c’est `Allocator()`.

Les deux premiers constructeurs spécifient une séquence contrôlée initiale vide.

Le troisième constructeur spécifie une répétition des éléments *Count* de la valeur `Type()` .

Les quatrième et cinquième constructeurs spécifient une répétition des éléments *Count* de la valeur *Val*.

Le sixième constructeur spécifie une copie de la séquence contrôlée par *Right*. Si `InputIterator` est un type entier, les deux constructeurs suivants spécifient une répétition des `(size_type)First` éléments ayant la valeur `(Type)Last`. Sinon, les deux constructeurs suivants spécifient la séquence `[First, Last)`.

Les neuvième et dixième constructeurs sont les mêmes que le sixième, mais avec une référence [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

Le dernier constructeur spécifie la séquence contrôlée initiale avec un objet de classe `initializer_list<Type>`.

## <a name="front"></a><a name="front"></a> frontal

Retourne une référence au premier élément d'un forward_list.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence au premier élément de la séquence contrôlée, qui ne doit pas être vide.

## <a name="get_allocator"></a><a name="get_allocator"></a> get_allocator

Retourne une copie de l'objet allocateur utilisé pour construire un forward_list.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet [allocateur](../standard-library/allocator-class.md) stocké.

## <a name="insert_after"></a><a name="insert_after"></a> insert_after

Ajoute des éléments au forward_list après une position spécifiée.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position dans la liste forward_list cible où le premier élément est inséré.

*Saut*\
Nombre d’éléments à insérer.

*Premier*\
Début de la plage d’insertion.

*Famille*\
Fin de la plage d’insertion.

*Multiples*\
Élément ajouté à la liste forward_list.

*IList*\
Initializer_list à insérer.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui désigne le nouvel élément inséré (première et deuxième fonctions membres uniquement).

### <a name="remarks"></a>Notes

Chacune des fonctions membres est insérée, juste après l’élément vers *lequel* pointe dans la séquence contrôlée, une séquence qui est spécifiée par les opérandes restants.

La première fonction membre insère un élément qui a une valeur *Val* et retourne un itérateur qui désigne l’élément nouvellement inséré.

La deuxième fonction membre insère une répétition des éléments *Count* de la valeur *Val*.

Si `InputIterator` est un type entier, la troisième fonction membre se comporte comme `insert(it, (size_type)First, (Type)Last)`. Sinon, elle insère la séquence `[First, Last)`, qui ne doit pas chevaucher la séquence contrôlée initiale.

La quatrième fonction membre insère la séquence spécifiée par un objet de classe `initializer_list<Type>`.

La dernière fonction membre est la même que la première, mais avec une référence [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

L’insertion de `N` éléments entraîne `N` appels de constructeur. Une [réallocation](../standard-library/forward-list-class.md) se produit, mais aucun itérateur ou référence ne devient non valide.

Si une exception est levée pendant l’insertion d’un ou plusieurs éléments, le conteneur n’est pas modifié et l’exception est levée de nouveau.

## <a name="iterator"></a><a name="iterator"></a> répétiteur

Type qui fournit un itérateur pour le forward_list.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Notes

`iterator` décrit un objet pouvant servir d’itérateur vers l’avant pour la séquence contrôlée. Il est décrit ici comme un synonyme du type défini par l’implémentation.

## <a name="max_size"></a><a name="max_size"></a> max_size

Retourne la longueur maximale d'un forward_list.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur de la séquence la plus longue que l’objet peut contrôler.

### <a name="remarks"></a>Notes

## <a name="merge"></a><a name="merge"></a> fusion

Combine les deux séquences triées en une seule séquence triée en temps linéaire. Supprime les éléments de la liste d’arguments et les insère dans ce `forward_list`. Les deux listes doivent être triées par le même objet de fonction de comparaison avant l’appel à `merge`. La liste combinée est triée par l’objet de fonction de comparaison.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Liste forward_list à partir de laquelle effectuer la fusion.

*conformes*\
Objet de fonction de comparaison utilisé pour trier les éléments.

### <a name="remarks"></a>Notes

`forward_list::merge` supprime les éléments de `forward_list` `right` et les insère dans ce `forward_list` . Les deux séquences doivent être triées par le même prédicat, décrit ci-dessous. La séquence combinée est également ordonnée par cet objet de fonction de comparaison.

Pour les itérateurs `Pi` et `Pj` désignant des éléments aux positions `i` et `j`, la première fonction membre impose l’ordre `!(*Pj < *Pi)` chaque fois que `i < j`. (Les éléments sont triés dans l' `ascending` ordre.) La deuxième fonction membre impose l’ordre `! comp(*Pj, *Pi)` chaque fois `i < j` .

Aucune paire d’éléments dans la séquence contrôlée d’origine n’est inversée dans la séquence contrôlée obtenue. Si deux éléments de la séquence contrôlée obtenue sont égaux ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), un élément de la séquence contrôlée d’origine apparaît avant un élément de la séquence contrôlée par `right`.

Une exception se produit uniquement si `comp` lève une exception. Dans ce cas, la séquence contrôlée conserve un ordre non spécifié et l’exception est levée de nouveau.

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Remplace les éléments du forward_list par une copie d'un autre forward_list.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Liste forward_list copiée dans la liste forward_list.

*IList*\
Liste d’initialiseurs entre accolades, qui se comporte comme une séquence d’éléments de type `Type`.

### <a name="remarks"></a>Notes

Le premier opérateur membre remplace la séquence contrôlée par une copie de la séquence contrôlée par *Right*.

Le deuxième opérateur membre remplace la séquence contrôlée à partir d’un objet de classe `initializer_list<Type>`.

Le troisième opérateur membre est le même que le premier, mais avec une référence [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="pointer"></a>Pointeur <a name="pointer"></a>

Type qui fournit un pointeur vers un élément du forward_list.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a><a name="pop_front"></a> pop_front

Supprime l'élément au début d'un forward_list.

```cpp
void pop_front();
```

### <a name="remarks"></a>Notes

Le premier élément de la liste forward_list ne doit pas être vide.

La fonction membre ne lève jamais d’exception.

## <a name="push_front"></a><a name="push_front"></a> push_front

Ajoute un élément au début d'un forward_list.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Élément ajouté au début de la liste forward_list.

### <a name="remarks"></a>Notes

Si une exception est levée, le conteneur n’est pas modifié et l’exception est levée de nouveau.

## <a name="reference"></a><a name="reference"></a> faire

Type qui fournit une référence à un élément du forward_list.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a><a name="remove"></a> Installez

Efface les éléments dans un forward_list qui correspond à une valeur spécifiée.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Paramètres

*multiples*\
Valeur qui, si elle est contenue dans un élément, entraîne la suppression de cet élément de la liste.

### <a name="remarks"></a>Notes

La fonction membre supprime de la séquence contrôlée tous les éléments désignés par l’itérateur `P` pour lesquels `*P ==  val`.

La fonction membre ne lève jamais d’exception.

## <a name="remove_if"></a><a name="remove_if"></a> remove_if

Efface les éléments d’un forward_list pour lequel un prédicat spécifié est satisfait.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>Paramètres

*prédit*\
Prédicat unaire qui, s’il est satisfait par un élément, entraîne la suppression de cet élément de la liste.

### <a name="remarks"></a>Notes

La fonction membre supprime de la séquence contrôlée tous les éléments désignés par l’itérateur `P` pour lesquels `pred(*P)` est true.

Une exception se produit uniquement si *prédit* lève une exception. Dans ce cas, la séquence contrôlée conserve un état non spécifié et l’exception est levée de nouveau.

## <a name="resize"></a><a name="resize"></a> redimensionner

Spécifie une nouvelle taille pour un forward_list.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Paramètres

*_Newsize*\
Nombre d’éléments dans la liste forward_list redimensionnée.

*multiples*\
Valeur à utiliser pour le remplissage.

### <a name="remarks"></a>Notes

Les fonctions membres garantissent que le nombre d’éléments dans la liste est *_Newsize*. Si la séquence contrôlée doit être plus longue, la première fonction membre ajoute des éléments avec `Type()` la valeur, tandis que la deuxième fonction membre ajoute des éléments avec la valeur *Val*. Pour raccourcir la séquence contrôlée, les deux fonctions membres appellent `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a><a name="reverse"></a> TVA

Inverse l'ordre dans lequel les éléments apparaissent dans un forward_list.

```cpp
void reverse();
```

## <a name="size_type"></a><a name="size_type"></a> size_type

Type qui représente la distance non signée entre deux éléments.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Notes

Le type d'entier non signé décrit un objet qui peut représenter la longueur de n'importe quelle séquence contrôlée.

## <a name="sort"></a><a name="sort"></a> Tris

Réorganise les éléments dans l’ordre croissant ou dans un ordre spécifié par un prédicat.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Paramètres

*prédit*\
Prédicat de tri.

### <a name="remarks"></a>Notes

Les deux fonctions membres ordonnent les éléments dans la séquence contrôlée selon un prédicat, décrit ci-dessous.

Pour les itérateurs `Pi` et `Pj` désignant des éléments aux positions `i` et `j`, la première fonction membre impose l’ordre `!(*Pj < *Pi)` chaque fois que `i < j`. (Les éléments sont triés dans l' `ascending` ordre.) La fonction de modèle membre impose l’ordre `! pred(*Pj, *Pi)` chaque fois `i < j` . Aucune paire d’éléments ordonnée dans la séquence contrôlée d’origine n’est inversée dans la séquence contrôlée obtenue. (Le tri est stable.)

Une exception se produit uniquement si *prédit* lève une exception. Dans ce cas, la séquence contrôlée conserve un ordre non spécifié et l’exception est levée de nouveau.

## <a name="splice_after"></a><a name="splice_after"></a> splice_after

Supprime des éléments d'une liste forward_list source et les insère dans une liste forward_list de destination.

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>Paramètres

*Cela*\
Position dans la liste forward_list de destination après laquelle l'insertion doit être effectuée.

*Code*\
Liste forward_list source qui doit être insérée dans la liste forward_list de destination.

*ITER*\
Élément à insérer à partir de la liste forward_list source.

*Premier*\
Premier élément de la plage à insérer à partir de la liste forward_list source.

*Famille*\
Première position au-delà de la plage à insérer à partir de la liste forward_list source.

### <a name="remarks"></a>Notes

La première paire de fonctions membres insère la séquence contrôlée par la *source* juste après l’élément dans la séquence contrôlée vers *laquelle* pointe. Elle supprime également tous les éléments de la *source*. ( `&Source` ne doit pas être égal à **`this`** .)

La deuxième paire de fonctions membres supprime l’élément juste après *ITER* dans la séquence contrôlée par la *source* et l’insère juste après l’élément dans la séquence contrôlée vers *laquelle* pointe. (Si `Where == Iter || Where == ++Iter`, aucune modification ne se produit.)

La troisième paire de fonctions membres (Splice étendue) insère la sous-plage désignée par `(First, Last)` à partir de la séquence contrôlée par la *source* juste après l’élément dans la séquence contrôlée vers *laquelle* pointe. Elle supprime également la sous-plage d’origine de la séquence contrôlée par la *source*. (Si `&Source == this` la valeur est, la plage `(First, Last)` ne doit pas inclure l’élément vers *lequel* pointe.)

Si la méthode splice à plage insère `N` éléments et que `&Source != this`, un objet de classe [iterator](#iterator) est incrémenté `N` fois.

Aucun itérateur, pointeur ou référence qui désigne des éléments ajoutés n'est invalidé.

### <a name="example"></a>Exemple

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux forward_list.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Liste forward_list qui fournit les éléments à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange les séquences contrôlées entre **`*this`** et *Right*. Si `get_allocator() ==  right.get_allocator()`, elle le fait en temps constant, ne lève aucune exception et n’invalide aucune référence, pointeur ou itérateur qui désigne des éléments dans les deux séquences contrôlées. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.

## <a name="unique"></a><a name="unique"></a> unique

Élimine tous les éléments sauf le premier de chaque groupe consécutif d’éléments égaux.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Paramètres

*conformes*\
Prédicat binaire utilisé pour comparer des éléments consécutifs.

### <a name="remarks"></a>Notes

Conserve le premier de chaque élément unique et supprime le reste. Les éléments doivent être triés pour que les éléments de valeur égale soient adjacents dans la liste.

La première fonction membre supprime de la séquence contrôlée chaque élément dont la valeur est égale à celle de l’élément précédent. Pour les itérateurs `Pi` et `Pj` désignant des éléments aux positions `i` et `j`, la deuxième fonction membre supprime chaque élément pour lequel `i + 1 == j &&  comp(*Pi, *Pj)`.

Pour une séquence contrôlée de longueur `N` (> 0), le prédicat `comp(*Pi, *Pj)` est évalué `N - 1` fois.

Une exception se produit uniquement si `comp` lève une exception. Dans ce cas, la séquence contrôlée conserve un état non spécifié et l’exception est levée de nouveau.

## <a name="value_type"></a><a name="value_type"></a> value_type

Type qui représente le type d'élément stocké dans un forward_list.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Type`.
