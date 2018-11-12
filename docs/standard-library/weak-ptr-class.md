---
title: weak_ptr, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 79869773591eee0a85cbc752be246bedb783bad2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462983"
---
# <a name="weakptr-class"></a>weak_ptr, classe

Encapsule un pointeur faiblement lié.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Ty>
   class weak_ptr {
public:
   typedef Ty element_type;
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type contrôlé par le pointeur faible.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui pointe vers une ressource gérée par un ou plusieurs objets [shared_ptr (classe)](../standard-library/shared-ptr-class.md). Les objets `weak_ptr` qui pointent vers une ressource n'affectent pas le décompte de références de la ressource. Ainsi, quand le dernier objet `shared_ptr` qui gère cette ressource est détruit, la ressource est libérée, même s'il existe des objets `weak_ptr` pointant vers cette ressource. Ceci est essentiel pour éviter les cycles de structures de données.

Un objet `weak_ptr` pointe vers une ressource s’il a été construit à partir d’un objet `shared_ptr` qui détient cette ressource, s’il a été construit à partir d’un objet `weak_ptr` qui pointe vers cette ressource ou si cette ressource lui a été assignée à l’aide d’[operator=](#op_eq). Un objet `weak_ptr` ne fournit pas un accès direct à la ressource vers laquelle il pointe. Le code qui a besoin d’utiliser la ressource le fait via un objet `shared_ptr` qui détient cette ressource, créé en appelant la fonction membre [lock](#lock). Un objet `weak_ptr` a expiré quand la ressource vers laquelle il pointe a été libérée car tous les objets `shared_ptr` détenant la ressource ont été détruits. L'appel de `lock` sur un objet `weak_ptr` qui a expiré crée un objet shared_ptr vide.

Un objet weak_ptr vide ne pointe vers aucune ressource et n'a aucun bloc de contrôle. Sa fonction membre `lock` retourne un objet shared_ptr vide.

Un cycle se produit quand plusieurs ressources contrôlées par des objets `shared_ptr` contiennent des objets `shared_ptr` qui se font référence mutuellement. Par exemple, une liste circulaire liée avec trois éléments a un nœud principal `N0` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N1` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N2` ; ce nœud, à son tour, contient un objet `shared_ptr` qui possède le nœud principal, `N0`, ce qui ferme le cycle. Dans cette situation, aucun des décomptes de références n'est jamais égal à zéro et les nœuds du cycle ne sont pas libérés. Pour éliminer le cycle, le dernier nœud `N2` doit contenir un objet `weak_ptr` pointant vers `N0` au lieu d'un objet `shared_ptr`. Puisque l'objet `weak_ptr` ne possède pas `N0`, il n'affecte pas le décompte de références de `N0` et quand la dernière référence du programme au nœud principal est détruite, les nœuds figurant dans la liste sont également détruits.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[weak_ptr](#weak_ptr)|Construit un objet `weak_ptr`.|

### <a name="methods"></a>Méthodes

|||
|-|-|
|[element_type](#element_type)|Type de l'élément.|
|[expired](#expired)|Teste si la propriété a expiré.|
|[lock](#lock)|Obtient la propriété exclusive d'une ressource.|
|[owner_before](#owner_before)|Retourne **true** si ce `weak_ptr` est classé avant (ou inférieur à) le pointeur fourni.|
|[reset](#reset)|Libère la ressource détenue.|
|[swap](#swap)|Échange deux objets `weak_ptr`.|
|[use_count](#use_count)|Compte le nombres d'objets `shared_ptr` désignés.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Remplace la ressource détenue.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="element_type"></a>  element_type

Type de l'élément.

```cpp
typedef Ty element_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Ty`.

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

## <a name="expired"></a>  expired

Teste si la propriété a expiré.

```cpp
bool expired() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne **true** si `*this` a expiré, sinon **false**.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

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

## <a name="lock"></a>  lock

Obtient la propriété exclusive d'une ressource.

```cpp
shared_ptr<Ty> lock() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne un objet shared_ptr vide si `*this` a expiré ; sinon, elle retourne un [shared_ptr, classe](../standard-library/shared-ptr-class.md)\<Ty > objet qui détient la ressource qui `*this` pointe vers.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

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

## <a name="op_eq"></a>  operator=

Remplace la ressource détenue.

```cpp
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Paramètres

*Autre*<br/>
Type contrôlé par le pointeur partagé/faible d’argument.

*WP*<br/>
Pointeur faible à copier.

*SP*<br/>
Pointeur partagé à copier.

### <a name="remarks"></a>Notes

Tous les opérateurs libèrent la ressource sur laquelle `*this` pointe actuellement, et assignent la propriété de la ressource nommée par la séquence d’opérandes à `*this`. Si un opérateur échoue, il laisse `*this` inchangé.

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

## <a name="owner_before"></a>  owner_before

Retourne **true** si ce `weak_ptr` est classé avant (ou inférieur à) le pointeur fourni.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Référence `lvalue` à un `shared_ptr` ou à un `weak_ptr`.

### <a name="remarks"></a>Notes

La fonction membre de modèle retourne **true** si `*this` est `ordered before` `ptr`.

## <a name="reset"></a>  reset

Libère la ressource détenue.

```cpp
void reset();
```

### <a name="remarks"></a>Notes

La fonction membre libère la ressource sur laquelle `*this` pointe et convertit `*this` en un objet weak_ptr vide.

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

## <a name="swap"></a>  swap

Échange deux objets `weak_ptr`.

```cpp
void swap(weak_ptr& wp);
```

### <a name="parameters"></a>Paramètres

*WP*<br/>
Pointeur faible à échanger.

### <a name="remarks"></a>Notes

La fonction membre laisse la ressource à l’origine vers lequel pointée `*this` par la suite vers lequel pointe *wp*et la ressource à l’origine vers lequel pointé *wp* par la suite vers lequel pointe `*this`. La fonction ne change pas les décomptes de références pour les deux ressources, et ne lève aucune exception.

### <a name="example"></a>Exemple

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

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

## <a name="use_count"></a>  use_count

Compte le nombres d'objets `shared_ptr` désignés.

```cpp
long use_count() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne le nombre d’objets `shared_ptr` qui détiennent la ressource désignée par `*this`.

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

## <a name="weak_ptr"></a>  weak_ptr

Construit un objet `weak_ptr`.

```cpp
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Paramètres

*Autre*<br/>
Type contrôlé par le pointeur partagé/faible d’argument.

*WP*<br/>
Pointeur faible à copier.

*SP*<br/>
Pointeur partagé à copier.

### <a name="remarks"></a>Notes

Chaque constructeur construit un objet qui pointe vers la ressource nommée par la séquence d’opérandes.

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

## <a name="see-also"></a>Voir aussi

[shared_ptr, classe](../standard-library/shared-ptr-class.md)<br/>
