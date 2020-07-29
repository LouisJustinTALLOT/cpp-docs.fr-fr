---
title: Allocateurs
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: 5aee23f72c5b0fb955b4dcc76a3f8c51eca7be70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204233"
---
# <a name="allocators"></a>Allocateurs

Les allocateurs sont utilisés par la bibliothèque C++ Standard pour gérer l’allocation et la désallocation des éléments stockés dans des conteneurs. Tous les conteneurs de bibliothèque C++ Standard sauf std::array ont un paramètre de modèle de type `allocator<Type>`, où `Type` représente le type de l’élément conteneur. Par exemple, la classe vector est déclarée comme suit :

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

La bibliothèque C++ Standard fournit une implémentation par défaut pour un allocateur. Dans C++11 et version supérieure, l’allocateur par défaut est mis à jour pour exposer une interface plus petite. Le nouvel allocateur est appelé *allocateur minimal*. En particulier, le membre `construct()` de l'allocateur minimal prend en charge la sémantique de déplacement, ce qui peut améliorer considérablement les performances. Dans la plupart des cas, cet allocateur par défaut suffit. Dans C++11, tous les types et les fonctions de la bibliothèque STL qui acceptent un paramètre de type allocateur prennent en charge l'interface d'allocateur minimal, y compris `std::function`, `shared_ptr, allocate_shared()` et `basic_string`.  Pour plus d’informations sur l’allocateur par défaut, consultez [allocator, classe](allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Écriture de votre propre allocateur (C++11)

L’allocateur par défaut utilise **`new`** et **`delete`** pour allouer et libérer de la mémoire. Si vous souhaitez utiliser une autre méthode d'allocation de la mémoire, telle que l'utilisation de la mémoire partagée, vous devez créer votre propre allocateur. Si vous ciblez C++11 et que vous devez écrire un nouvel allocateur personnalisé, faites-en un allocateur minimal si possible. Même si vous avez déjà implémenté un allocateur de style antérieur, changez-le en *allocateur minimal* pour tirer parti de la méthode `construct()` la plus efficace fournie automatiquement.

Un allocateur minimal nécessite beaucoup moins de code réutilisable et vous permet de vous concentrer sur les fonctions membres `allocate` et `deallocate` qui effectuent tout le travail. Lors de la création d'un allocateur minimal, n'implémentez aucun membre à l'exception de ceux indiqués dans l'exemple ci-dessous :

1. un constructeur de copie de conversion (voir l'exemple)

1. opérateur ==

1. !=, opérateur

1. allocate

1. deallocate

Le membre `construct()` par défaut dans C++11 qui vous sera fourni effectue un transfert parfait et autorise la sémantique de déplacement. Dans de nombreux cas, il est beaucoup plus efficace que l'ancienne version.

> [!WARNING]
> Au moment de la compilation, la bibliothèque C++ Standard utilise la classe allocator_traits pour détecter les membres que vous avez fournis explicitement et fournit une implémentation par défaut pour tous les membres qui ne sont pas présents. N'interférez pas avec ce mécanisme en fournissant une spécialisation d'allocator_traits pour votre allocateur.

L'exemple suivant montre une implémentation minimale d'un allocateur qui utilise `malloc` et `free`. Notez l'utilisation du nouveau type d'exception `std::bad_array_new_length` qui est levé si la taille du tableau est inférieure à zéro ou supérieure à la taille maximale autorisée.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>Écriture de votre propre allocateur (C++03)

Dans C++03, tout allocateur utilisé avec des conteneurs de bibliothèque C++ Standard doit implémenter les définitions de types suivantes :

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Par ailleurs, tout allocateur utilisé avec des conteneurs de bibliothèque C++ Standard doit implémenter les méthodes suivantes :

|||
|-|-|
|Constructeur|`deallocate`|
|Constructeur de copie|`destroy`|
|Destructeur|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Pour plus d’informations sur ces méthodes et définitions de types, consultez [allocator, classe](allocator-class.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque C++ standard](cpp-standard-library-reference.md)
