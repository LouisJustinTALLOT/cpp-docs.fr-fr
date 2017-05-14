---
title: weak_ptr, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- weak_ptr
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
dev_langs:
- C++
helpviewer_keywords:
- weak_ptr class
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: f7e4ff26f4d98dc677483f8526c17474aecc81dc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="weakptr-class"></a>weak_ptr, classe
Encapsule un pointeur faiblement lié.  
  
## <a name="syntax"></a>Syntaxe  
```    
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
#### <a name="parameters"></a>Paramètres  
 `Ty`  
 Type contrôlé par le pointeur faible.  
  
## <a name="remarks"></a>Notes  
 La classe de modèle décrit un objet qui pointe vers une ressource gérée par un ou plusieurs objets [shared_ptr (classe)](../standard-library/shared-ptr-class.md). Les objets `weak_ptr` qui pointent vers une ressource n'affectent pas le décompte de références de la ressource. Ainsi, quand le dernier objet `shared_ptr` qui gère cette ressource est détruit, la ressource est libérée, même s'il existe des objets `weak_ptr` pointant vers cette ressource. Ceci est essentiel pour éviter les cycles de structures de données.  
  
 Un objet `weak_ptr` pointe vers une ressource s’il a été construit à partir d’un objet `shared_ptr` qui détient cette ressource, s’il a été construit à partir d’un objet `weak_ptr` qui pointe vers cette ressource ou si cette ressource lui a été assignée à l’aide d’[operator=](#op_eq). Un objet `weak_ptr` ne fournit pas un accès direct à la ressource vers laquelle il pointe. Le code qui a besoin d’utiliser la ressource le fait via un objet `shared_ptr` qui détient cette ressource, créé en appelant la fonction membre [lock](#lock). Un objet `weak_ptr` a expiré quand la ressource vers laquelle il pointe a été libérée car tous les objets `shared_ptr` détenant la ressource ont été détruits. L'appel de `lock` sur un objet `weak_ptr` qui a expiré crée un objet shared_ptr vide.  
  
 Un objet weak_ptr vide ne pointe vers aucune ressource et n'a aucun bloc de contrôle. Sa fonction membre `lock` retourne un objet shared_ptr vide.  
  
 Un cycle se produit quand plusieurs ressources contrôlées par des objets `shared_ptr` contiennent des objets `shared_ptr` qui se font référence mutuellement. Par exemple, une liste circulaire liée avec trois éléments a un nœud principal `N0` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N1` ; ce nœud contient un objet `shared_ptr` qui possède le nœud suivant, `N2` ; ce nœud, à son tour, contient un objet `shared_ptr` qui possède le nœud principal, `N0`, ce qui ferme le cycle. Dans cette situation, aucun des décomptes de références n'est jamais égal à zéro et les nœuds du cycle ne sont pas libérés. Pour éliminer le cycle, le dernier nœud `N2` doit contenir un objet `weak_ptr` pointant vers `N0` au lieu d'un objet `shared_ptr`. Puisque l'objet `weak_ptr` ne possède pas `N0`, il n'affecte pas le décompte de références de `N0` et quand la dernière référence du programme au nœud principal est détruite, les nœuds figurant dans la liste sont également détruits.  
  
## <a name="members"></a>Membres  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[weak_ptr](#weak_ptr)|Construit un objet `weak_ptr`.|  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[element_type](#element_type)|Type de l'élément.|  
|[expired](#expired)|Teste si la propriété a expiré.|  
|[lock](#lock)|Obtient la propriété exclusive d'une ressource.|  
|[owner_before](#owner_before)|Retourne `true` si ce `weak_ptr` est classé avant le pointeur fourni (ou est inférieur à celui-ci).|  
|[reset](#reset)|Libère la ressource détenue.|  
|[swap](#swap)|Échange deux objets `weak_ptr`.|  
|[use_count](#use_count)|Compte le nombres d'objets `shared_ptr` désignés.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator=](#op_eq)|Remplace la ressource détenue.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<memory>  
  
 **Espace de noms :** std  
  
##  <a name="element_type"></a>  element_type  
 Type de l'élément.  
  
```  
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
  
##  <a name="expired"></a>  expired  
 Teste si la propriété a expiré.  
  
```  
bool expired() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne `true` si `*this` a expiré, sinon `false`.  
  
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
  
##  <a name="lock"></a>  lock  
 Obtient la propriété exclusive d'une ressource.  
  
```  
shared_ptr<Ty> lock() const;
```  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un objet shared_ptr vide si `*this` a expiré ; sinon, elle retourne un objet [shared_ptr (classe)](../standard-library/shared-ptr-class.md)`<Ty>` qui détient la ressource vers laquelle `*this` pointe.  
  
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
  
##  <a name="op_eq"></a>  operator=  
 Remplace la ressource détenue.  
  
```  
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>  
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr& operator=(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Paramètres  
 `Other`  
 Type contrôlé par le pointeur partagé/faible d’argument.  
  
 `wp`  
 Pointeur faible à copier.  
  
 `sp`  
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
  
##  <a name="owner_before"></a>  owner_before  
 Retourne `true` si ce `weak_ptr` est classé avant le pointeur fourni (ou est inférieur à celui-ci).  
  
```  
template <class Other>  
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>  
bool owner_before(const weak_ptr<Other>& ptr);
```  
  
### <a name="parameters"></a>Paramètres  
 `ptr`  
 Référence `lvalue` à un `shared_ptr` ou à un `weak_ptr`.  
  
### <a name="remarks"></a>Notes  
 La fonction membre de modèle retourne `true` si `*this` est `ordered before``ptr`.  
  
##  <a name="reset"></a>  reset  
 Libère la ressource détenue.  
  
```  
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
  
##  <a name="swap"></a>  swap  
 Échange deux objets `weak_ptr`.  
  
```  
void swap(weak_ptr& wp);
```  
  
### <a name="parameters"></a>Paramètres  
 `wp`  
 Pointeur faible à échanger.  
  
### <a name="remarks"></a>Notes  
 La fonction membre laisse la ressource désignée à l’origine par `*this` être ensuite désignée par `wp`, et la ressource désignée à l’origine par `wp` être ensuite désignée par `*this`. La fonction ne change pas les décomptes de références pour les deux ressources, et ne lève aucune exception.  
  
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
  
##  <a name="use_count"></a>  use_count  
 Compte le nombres d'objets `shared_ptr` désignés.  
  
```  
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
  
##  <a name="weak_ptr"></a>  weak_ptr  
 Construit un objet `weak_ptr`.  
  
```  
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>  
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Paramètres  
 `Other`  
 Type contrôlé par le pointeur partagé/faible d’argument.  
  
 `wp`  
 Pointeur faible à copier.  
  
 `sp`  
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
 [shared_ptr, classe](../standard-library/shared-ptr-class.md)


