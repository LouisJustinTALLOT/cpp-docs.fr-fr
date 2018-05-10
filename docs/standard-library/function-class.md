---
title: function, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26164c391689c8fb7f24f49464e141f74a3058ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="function-class"></a>function, classe

Wrapper pour un objet pouvant être appelé.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>Paramètres

`Fty` Le type de fonction à encapsuler.

`Ax` La fonction de l’allocateur.

## <a name="remarks"></a>Notes

La classe de modèle est un wrapper d’appel dont la signature d’appel est `Ret(T1, T2, ..., TN)`. Vous l’utiliser pour placer divers objets pouvant être appelés dans un wrapper uniforme.

Certaines fonctions membres acceptent un opérande qui nomme l’objet cible souhaité. Vous pouvez spécifier cet opérande de plusieurs façons :

`fn` : objet pouvant être appelé `fn` ; après l’appel, l’objet `function` contient une copie de `fn`

`fnref` : objet pouvant être appelé nommé par `fnref.get()` ; après l’appel, l’objet `function` contient une référence à `fnref.get()`

`right` : objet pouvant être appelé, le cas échéant, contenu par l’objet `function` `right`

`npc` : pointeur null ; après l’appel, l’objet `function` est vide

Dans tous les cas, `INVOKE(f, t1, t2, ..., tN)`, où `f` est l’objet pouvant être appelé et `t1, t2, ..., tN` sont des lvalues de types `T1, T2, ..., TN` respectivement, doit être correctement construit et, si `Ret` n’est pas vide, convertible en `Ret`.

Un objet `function` vide ne contient pas d’objet pouvant être appelé ou de référence à un objet pouvant être appelé.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[function](#function)|Construit un wrapper qui est vide ou stocke un objet pouvant être appelé de type arbitraire avec une signature fixe.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[result_type](#result_type)|Type de retour de l’objet pouvant être appelé stocké.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[assign](#assign)|Assigne un objet pouvant être appelé à cet objet de fonction.|
|[swap](#swap)|Échange deux objets pouvant être appelés.|
|[target](#target)|Vérifie si l’objet pouvant être appelé stocké peut être appelé comme spécifié.|
|[target_type](#target_type)|Obtient les informations de type sur l'objet pouvant être appelé.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[function::operator unspecified](#op_unspecified)|Vérifie si l’objet pouvant être appelé stocké existe.|
|[function::operator()](#op_call)|Appelle un objet pouvant être appelé.|
|[function::operator=](#op_eq)|Remplace l’objet pouvant être appelé stocké.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="assign"></a>  function::assign

Assigne un objet pouvant être appelé à cet objet de fonction.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Paramètres

`_Func` Un objet pouvant être appelé.

`_Fnref` Un wrapper de référence qui contient un objet pouvant être appelé.

`Ax` Un objet allocateur.

### <a name="remarks"></a>Notes

Les fonctions membres remplacent chacune le `callable object` contenu dans `*this` par l’objet pouvant être appelé passé comme `operand`. Les deux fonctions allouent du stockage avec l’objet allocateur `Ax`.

## <a name="function"></a>  function::function

Construit un wrapper qui est vide ou stocke un objet pouvant être appelé de type arbitraire avec une signature fixe.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Paramètres

`right` L’objet de fonction à copier.

`Fx` Le type de l’objet peut être appelé.

`_Func` Objet pouvant être appelé à encapsuler.

`Alloc` Le type d’allocateur.

`Ax` L’allocateur.

`_Fnref` La référence d’objet pouvant être appelé à encapsuler.

### <a name="remarks"></a>Notes

Les deux premiers constructeurs construisent un objet `function` vide. Les trois constructeurs suivants construisent un objet `function` qui contient l’objet pouvant être appelé passé comme opérande. Les deux derniers constructeurs allouent du stockage avec l’objet allocateur Ax.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="op_unspecified"></a>  function::operator unspecified

Vérifie si l’objet pouvant être appelé stocké existe.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en `bool` avec une valeur true uniquement si l’objet n’est pas vide. Vous l’utilisez pour vérifier si l’objet est vide.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="op_call"></a>  function::operator()

Appelle un objet pouvant être appelé.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Paramètres

`TN` Le type du nième appeler argument.

`tN` L’argument d’appel nième.

### <a name="remarks"></a>Notes

La fonction membre retourne `INVOKE(fn, t1, t2, ..., tN, Ret)`, où `fn` est l’objet cible stocké dans `*this`. Vous l’utiliser pour appeler l’objet pouvant être appelé inclus dans un wrapper.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="op_eq"></a>  function::operator=

Remplace l’objet pouvant être appelé stocké.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Paramètres

`npc` Une constante pointeur null.

`right` L’objet de fonction à copier.

`fn` Objet pouvant être appelé à encapsuler.

`fnref` La référence d’objet pouvant être appelé à encapsuler.

### <a name="remarks"></a>Notes

Les opérateurs remplacent chacun l’objet pouvant être appelé contenu dans `*this` par l’objet pouvant être appelé passé comme opérande.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_operator_as.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a>  function::result_type

Type de retour de l’objet pouvant être appelé stocké.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme du type `Ret` dans la signature d’appel du modèle. Vous l’utilisez pour déterminer le type de retour de l’objet pouvant être appelé inclus dans un wrapper.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a>  function::swap

Échange deux objets pouvant être appelés.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Paramètres

`right` L’objet de fonction à échanger.

### <a name="remarks"></a>Notes

La fonction membre échange les objets cibles de `*this` et `right`. Elle le fait dans un cadre de temps fixe, et ne lève aucune exception.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    fn0.swap(fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```

## <a name="target"></a>  function::target

Vérifie si l’objet pouvant être appelé stocké peut être appelé comme spécifié.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Paramètres

`Fty2` Le type d’objet pouvant être appelé cible à tester.

### <a name="remarks"></a>Notes

Le type `Fty2` doit pouvoir être appelé pour les types d’argument `T1, T2, ..., TN` et le type de retour `Ret`. Si `target_type() == typeid(Fty2)`, la fonction de modèle membre retourne l’adresse de l’objet cible ; sinon, elle retourne 0.

Un type `Fty2` peut être appelé pour les types d’argument `T1, T2, ..., TN` et le type de retour `Ret` si, pour les lvalues `fn, t1, t2, ..., tN` de types `Fty2, T1, T2, ..., TN`, respectivement, `INVOKE(fn, t1, t2, ..., tN)` est correct et, si `Ret` n’est pas `void`, convertible en `Ret`.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }

```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a>  function::target_type

Obtient les informations de type sur l'objet pouvant être appelé.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `typeid(void)` si `*this` est vide. Sinon, elle retourne `typeid(T)`, où `T` est le type de l'objet cible.

### <a name="example"></a>Exemple

```cpp
// std__functional__function_target_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```

## <a name="see-also"></a>Voir aussi

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper, classe](../standard-library/reference-wrapper-class.md)<br/>
