---
title: weak_ptr, classe
ms.date: 07/29/2019
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: f76682b14e49e5f699144674da33b0826975e2d6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217335"
---
# <a name="weak_ptr-class"></a>weak_ptr, classe

Encapsule un pointeur faiblement lié.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Paramètres

*T*\
Type contrôlé par le pointeur faible.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui pointe vers une ressource gérée par un ou plusieurs objets [shared_ptr](shared-ptr-class.md) . Les `weak_ptr` objets qui pointent vers une ressource n’affectent pas le nombre de références de la ressource. Lorsque le dernier `shared_ptr` objet qui gère cette ressource est détruit, la ressource est libérée, même s’il existe des `weak_ptr` objets pointant vers cette ressource. Ce comportement est essentiel pour éviter les cycles dans les structures de données.

Un objet `weak_ptr` pointe vers une ressource s’il a été construit à partir d’un objet `shared_ptr` qui détient cette ressource, s’il a été construit à partir d’un objet `weak_ptr` qui pointe vers cette ressource ou si cette ressource lui a été assignée à l’aide d’[operator=](#op_eq). Un `weak_ptr` objet ne fournit pas un accès direct à la ressource vers laquelle il pointe. Le code qui a besoin d’utiliser la ressource le fait via un objet `shared_ptr` qui détient cette ressource, créé en appelant la fonction membre [lock](#lock). Un `weak_ptr` objet a expiré quand la ressource vers laquelle il pointe a été libérée car tous les `shared_ptr` objets qui le possèdent ont été détruits. L'appel de `lock` sur un objet `weak_ptr` qui a expiré crée un objet shared_ptr vide.

Un objet weak_ptr vide ne pointe vers aucune ressource et n’a aucun bloc de contrôle. Sa fonction membre `lock` retourne un objet shared_ptr vide.

Un cycle se produit quand plusieurs ressources contrôlées par des objets `shared_ptr` contiennent des objets `shared_ptr` qui se font référence mutuellement. Par exemple, une liste circulaire liée avec trois éléments a un nœud principal `N0` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N1` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N2` ; ce nœud, à son tour, contient un objet `shared_ptr` qui possède le nœud principal, `N0`, ce qui ferme le cycle. Dans ce cas, le nombre de références ne devient jamais égal à zéro et les nœuds du cycle ne sont jamais libérés. Pour éliminer le cycle, le dernier nœud `N2` doit contenir un objet `weak_ptr` pointant vers `N0` au lieu d'un objet `shared_ptr`. Étant donné que l' `weak_ptr` objet n’est pas propriétaire `N0` , il n’affecte pas le `N0` décompte de références de et quand la dernière référence du programme au nœud principal est détruite, les nœuds de la liste sont également détruits.

## <a name="members"></a>Membres

|||
|-|-|
| **Constructeurs** | |
|[weak_ptr](#weak_ptr)|Construit un objet `weak_ptr`.|
| **Destructeurs** | |
|[~ weak_ptr](#tilde-weak_ptr)|Construit un objet `weak_ptr`.|
| **Typedefs** | |
|[element_type](#element_type)|Type de l'élément.|
| **Fonctions membres** | |
|[fin](#expired)|Teste si la propriété a expiré.|
|[Lock](#lock)|Obtient la propriété exclusive d'une ressource.|
|[owner_before](#owner_before)|Retourne **`true`** si ce `weak_ptr` est classé avant (ou inférieur à) le pointeur fourni.|
|[reset](#reset)|Libère la ressource détenue.|
|[swap](#swap)|Échange deux objets `weak_ptr`.|
|[use_count](#use_count)|Compte le nombre d' `shared_ptr` objets.|
| **Opérateurs** | |
|[opérateur =](#op_eq)|Remplace la ressource détenue.|

## <a name="element_type"></a><a name="element_type"></a>element_type

Type de l'élément.

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `T`.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a><a name="expired"></a>fin

Teste si la propriété a expiré, autrement dit si l’objet référencé a été supprimé.

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre retourne **`true`** si **`*this`** a expiré ; sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a><a name="lock"></a>Lock

Obtient un `shared_ptr` qui partage la propriété d’une ressource.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre retourne un objet [shared_ptr](shared-ptr-class.md) vide si **`*this`** a expiré ; sinon, elle retourne un `shared_ptr<T>` objet qui possède la ressource **`*this`** vers laquelle pointe. Retourne une valeur équivalente à l’exécution atomique de `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)` .

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="operator"></a><a name="op_eq"></a>opérateur =

Remplace la ressource détenue.

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Type contrôlé par l’argument de pointeur partagé ou faible.

*effectués*\
Pointeur faible ou pointeur partagé à copier.

### <a name="remarks"></a>Notes

Les opérateurs libèrent tous la ressource actuellement vers laquelle pointe **`*this`** et attribuent la propriété de la ressource nommée par *ptr* à **`*this`** . Si un opérateur échoue, il reste **`*this`** inchangé. Chaque opérateur a un effet équivalent à `weak_ptr(ptr).swap(*this)` .

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a><a name="owner_before"></a>owner_before

Retourne **`true`** si ce `weak_ptr` est classé avant (ou inférieur à) le pointeur fourni.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Paramètres

*effectués*\
Une référence lvalue à un `shared_ptr` ou un `weak_ptr` .

### <a name="remarks"></a>Notes

La fonction membre de modèle retourne **`true`** si **`*this`** est ordonné avant *ptr*.

## <a name="reset"></a><a name="reset"></a>initialisation

Libère la ressource détenue.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre libère la ressource vers laquelle pointe **`*this`** et la convertit en **`*this`** un `weak_ptr` objet vide.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a><a name="swap"></a>échange

Échange deux objets `weak_ptr`.

```cpp
void swap(weak_ptr& wp) noexcept;
```

Comprend également la spécialisation :

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Paramètres

*EP*\
Pointeur faible à échanger.

### <a name="remarks"></a>Notes

Après un `swap` , la ressource vers laquelle pointe la première fois **`*this`** est pointée par *WP*, et la ressource vers laquelle pointe *WP* est désignée par **`*this`** . La fonction ne modifie pas le nombre de références pour les deux ressources et ne lève aucune exception. L’effet de la spécialisation de modèle est l’équivalent de `a.swap(b)` .

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="use_count"></a><a name="use_count"></a>use_count

Compte le nombre d' `shared_ptr` objets qui possèdent la ressource partagée.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d' `shared_ptr` objets qui détiennent la ressource vers laquelle pointe **`*this`** .

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a><a name="weak_ptr"></a>weak_ptr

Construit un objet `weak_ptr`.

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Type contrôlé par le pointeur partagé/faible d’argument. Ces constructeurs ne participent pas à la résolution de surcharge, sauf si d' _autres \* _ sont compatibles avec `element_type*` .

*EP*\
Pointeur faible à copier.

*SR*\
Pointeur partagé à copier.

### <a name="remarks"></a>Notes

Le constructeur par défaut construit un `weak_ptr` objet vide. Les constructeurs qui acceptent chacun un argument construisent chacun un `weak_ptr` objet vide si le pointeur d’argument est vide. Dans le cas contraire, ils construisent un `weak_ptr` objet qui pointe vers la ressource nommée par l’argument. Le décompte de références de l’objet partagé n’est pas modifié.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="weak_ptr"></a><a name="tilde-weak_ptr"></a>~ weak_ptr

Détruit un `weak_ptr`.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Notes

Le destructeur détruit cela `weak_ptr` , mais n’a aucun effet sur le décompte de références de l’objet sur lequel son pointeur stocké pointe.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[shared_ptr, classe](shared-ptr-class.md)
