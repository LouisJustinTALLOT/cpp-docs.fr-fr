---
title: '&lt;functional&gt;, fonctions'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
ms.openlocfilehash: 546d8c61e875dd7c295e892359e39fa5a76867b4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243777"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt;, fonctions

Ces fonctions sont déconseillées dans C ++ 11 et supprimées dans C ++ 17 :

||||
|-|-|-|
|[bind1st](#bind1st) |[bind2nd](#bind2nd)|[mem_fun](#mem_fun)|
|[mem_fun_ref](#mem_fun_ref)|[ptr_fun](#ptr_fun)||

Ces fonctions sont déconseillées dans C ++ 17 :

|||
|-|-|
|[not1](#not1)|[not2](#not2)|

## <a name="bind"></a> Lier

Lie des arguments à un objet pouvant être appelé.

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Paramètres

*Fey*\
Type de l’objet à appeler.

*TN*\
Type du N-ième argument de l’appel.

*fn*\
Objet à appeler.

*tN*\
N-ième argument de l’appel.

### <a name="remarks"></a>Notes

Les types `FT, T1, T2, ..., TN` doit être constructible de copie, et `INVOKE(fn, t1, ..., tN)` doit être une expression valide pour certaines valeurs `w1, w2, ..., wN`.

La première fonction de modèle retourne un wrapper d’appel de transfert `g` avec un type de résultat faible. L’effet de `g(u1, u2, ..., uM)` est `INVOKE(f, v1, v2, ..., vN, ` [invoke_result](../standard-library/invoke-result-class.md)`<FT cv (V1, V2, ..., VN)>::type)`, où `cv` désigne les qualificateurs cv de `g` et les valeurs et les types des arguments liés `v1, v2, ..., vN` sont déterminées comme indiqué ci-dessous. Vous l’utilisez pour lier des arguments à un objet pouvant être appelé afin de créer un objet pouvant être appelé avec une liste d’arguments personnalisés.

La deuxième fonction de modèle retourne un wrapper d’appel de transfert `g` avec un type imbriqué `result_type` qui est un synonyme de `RTy`. L’effet de `g(u1, u2, ..., uM)` est `INVOKE(f, v1, v2, ..., vN, RTy)`, où `cv` désigne les qualificateurs cv de `g`, et les valeurs et types des arguments liés `v1, v2, ..., vN` sont déterminés comme indiqué ci-dessous. Vous l’utilisez pour lier des arguments à un objet pouvant être appelé afin de créer un objet pouvant être appelé avec une liste d’arguments personnalisés et un type de retour spécifié.

Les valeurs des arguments liés `v1, v2, ..., vN` et leurs types correspondants `V1, V2, ..., VN` dépendent du type de l’argument correspondant `ti` de type `Ti` dans l’appel à `bind` et des qualificateurs cv `cv` du wrapper d’appel `g` comme suit :

si `ti` est de type `reference_wrapper<T>`, l’argument `vi` est `ti.get()` et son type `Vi` est `T&` ;

Si la valeur de `std::is_bind_expression<Ti>::value` est **true** l’argument `vi` est `ti(u1, u2, ..., uM)` et son type `Vi` est `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Si la valeur `j` de `std::is_placeholder<Ti>::value` n’est pas égal à zéro de l’argument `vi` est `uj` et son type `Vi` est `Uj&`;

sinon l’argument `vi` est `ti` et son type `Vi` est `Ti` `cv` `&`.

Par exemple, avec une fonction `f(int, int)`, l’expression `bind(f, _1, 0)` retourne un wrappel d’appel de transfert `cw` de sorte que `cw(x)` appelle `f(x, 0)`. L’expression `bind(f, 0, _1)` retourne un wrapper d’appel de transfert `cw` de sorte que `cw(x)` appelle `f(0, x)`.

Le nombre d’arguments dans un appel à `bind` et l’argument `fn` doit être égal au nombre d’arguments qui peut être passé à l’objet pouvant être `fn`. Par exemple, `bind(cos, 1.0)` est correct et les deux `bind(cos)` et `bind(cos, _1, 0.0)` sont incorrectes.

Le nombre d’arguments dans l’appel de la fonction au wrapper d’appel retourné par `bind` doit être au moins aussi grand que la valeur numérotée la plus élevée de `is_placeholder<PH>::value` pour tous les arguments d’espace réservé dans l’appel à `bind`. Par exemple, `bind(cos, _2)(0.0, 1.0)` est correct (et retourne `cos(1.0)`), et `bind(cos, _2)(0.0)` est incorrect.

### <a name="example"></a>Exemples

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}
```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a> bind1st

Une fonction de modèle d’assistance qui crée un adaptateur pour convertir un objet de fonction binaire en objet de fonction unaire. Il lie le premier argument de la fonction binaire à une valeur spécifiée. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Paramètres

*Func*\
Objet de fonction binaire à convertir en un objet de fonction unaire.

*Gauche*\
Valeur à laquelle le premier argument de l’objet de fonction binaire doit être lié.

### <a name="return-value"></a>Valeur de retour

L’objet de fonction unaire qui résulte de la liaison du premier argument de l’objet de fonction binaire à la valeur *gauche*.

### <a name="remarks"></a>Notes

Binders de fonction sont un type d’adaptateur de fonction. Car elles renvoient des objets de fonction, elles peuvent servir dans certains types de composition de fonction pour construire des expressions plus complexes et puissantes.

Si *func* est un objet de type `Operation` et `c` est une constante, puis `bind1st( func, c )` est identique à la [binder1st](../standard-library/binder1st-class.md) constructeur de classe `binder1st<Operation>(func, c)`et est plus pratique utiliser.

### <a name="example"></a>Exemples

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a> bind2nd

Une fonction de modèle d’assistance qui crée un adaptateur pour convertir un objet de fonction binaire en objet de fonction unaire. Il lie le deuxième argument de la fonction binaire à une valeur spécifiée. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Paramètres

*Func*\
Objet de fonction binaire à convertir en un objet de fonction unaire.

*Oui*\
Valeur à laquelle le deuxième argument de l’objet de fonction binaire doit être lié.

### <a name="return-value"></a>Valeur de retour

Le résultat d’objet de fonction unaire de liant le second argument de l’objet de fonction binaire à *droit*.

### <a name="remarks"></a>Notes

Binders de fonction sont un type d’adaptateur de fonction. Car elles renvoient des objets de fonction, elles peuvent servir dans certains types de composition de fonction pour construire des expressions plus complexes et puissantes.

Si *func* est un objet de type `Operation` et `c` est une constante, puis `bind2nd(func, c)` est identique à la [binder2nd](../standard-library/binder2nd-class.md) constructeur de classe `binder2nd<Operation>(func, c)`et plus pratique à utiliser.

### <a name="example"></a>Exemple

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a> bit_and

Un objet de fonction prédéfini qui effectue une opération AND au niveau du bit (binaire `operator&`) sur ses arguments.

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator&` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération AND au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Oui*\
Opérande droit de l’opération AND au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left & Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator&`.

### <a name="remarks"></a>Notes

Le foncteur `bit_and` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator&` binaire.

## <a name="bit_not"></a> bit_not

Un objet de fonction prédéfini qui effectue un complément au niveau du bit de l’opération (NOT) (unaire `operator~`) sur ses arguments. Ajouté dans C ++ 14.

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
{
    Type operator()(const Type& Right) const;
};

// specialized transparent functor for operator~
template <>
struct bit_not<void>
{
    template <class Type>
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*\
Type prenant en charge un `operator~` unaire.

*Oui*\
Opérande de l’opération de complément au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert d’un argument de référence lvalue ou rvalue du type inféré parfait *Type*.

### <a name="return-value"></a>Valeur de retour

Résultat de `~ Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator~`.

### <a name="remarks"></a>Notes

Le foncteur `bit_not` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator~` binaire.

## <a name="bit_or"></a> bit_or

Un objet de fonction prédéfini qui effectue une opération OR au niveau du bit (`operator|`) sur ses arguments.

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator|` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération OR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Oui*\
Opérande droit de l’opération OR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left | Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator|`.

### <a name="remarks"></a>Notes

Le foncteur `bit_or` est limité aux types intégraux pour les types de données de base ou aux types définis par l'utilisateur qui implémentent `operator|`.

## <a name="bit_xor"></a> BIT_XOR

Un objet de fonction prédéfini qui effectue une opération de bits XOR (binaire `operator^`) sur ses arguments.

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
};

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator^` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération XOR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Oui*\
Opérande droit de l’opération XOR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left ^ Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator^`.

### <a name="remarks"></a>Notes

Le foncteur `bit_xor` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator^` binaire.

## <a name="cref"></a> cref

Construit un `reference_wrapper` const à partir d'un argument.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type de l’argument à inclure dans un wrapper.

*arg*\
Argument à inclure dans un wrapper.

### <a name="remarks"></a>Notes

La première fonction retourne `reference_wrapper<const Ty>(arg.get())`. Vous l’utilisez pour inclure une référence const dans un wrapper. La deuxième fonction retourne `reference_wrapper<const Ty>(arg)`. Vous l’utilisez pour inclure dans un wrapper une référence déjà incluse dans un wrapper comme référence const.

### <a name="example"></a>Exemples

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }
```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="invoke"></a> Appeler

Appelle un objet pouvant être appelé avec les arguments donnés. Ajouté dans C ++ 17.

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>Paramètres

*pouvant être appelé*\
Type de l’objet à appeler.

*args*\
Les types des arguments d’appel.

*fn*\
Objet à appeler.

*args*\
Arguments d'appel.

*spécification*\
Le **noexcept** spécification `std::is_nothrow_invocable_v<Callable, Args>)`.

### <a name="remarks"></a>Notes

Appelle l’objet pouvant être *fn* en utilisant les paramètres *args*. En effet, `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)`, où la pseudo-fonction `INVOKE(f, t1, t2, ..., tN)` peut être l’une des opérations suivantes :

- `(t1.*f)(t2, ..., tN)` quand `f` est un pointeur vers une fonction membre de classe `T` et `t1` est un objet de type `T` ou une référence à un objet de type `T` ou une référence à un objet d'un type dérivé de `T`. Autrement dit, lorsque `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` a la valeur true.

- `(t1.get().*f)(t2, ..., tN)` Lorsque `f` est un pointeur vers fonction membre de classe `T` et `std::decay_t<decltype(t1)>` est une spécialisation de `std::reference_wrapper`.

- `((*t1).*f)(t2, ..., tN)` Lorsque `f` est un pointeur vers fonction membre de classe `T` et `t1` ne sont pas des types précédents.

- `t1.*f` quand N == 1 et `f` est un pointeur vers des données de membre d'une classe `T` et `t1` est un objet de type `T` ou une référence à un objet de type `T` ou une référence à un objet d'un type dérivé de `T`.  Autrement dit, lorsque `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` a la valeur true.

- `t1.get().*f` quand N == 1 et `f` est un pointeur vers les données de membre d’une classe `T` et `std::decay_t<decltype(t1)>` est une spécialisation de `std::reference_wrapper`.

- `(*t1).*f` quand N == 1 et `f` est un pointeur vers les données de membre d’une classe `T` et `t1` ne sont pas des types précédents.

- `f(t1, t2, ..., tN)` dans tous les autres cas.

Pour plus d’informations sur le type de résultat d’un objet pouvant être appelé, consultez [invoke_result](invoke-result-class.md). Pour les prédicats sur les types pouvant être appelés, consultez [is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r classes](is-invocable-classes.md).

### <a name="example"></a>Exemples

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a> mem_fn

Génère un wrapper d'appel simple.

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>Paramètres

*RTy*\
Type de retour de la fonction incluse dans un wrapper.

*Ty*\
Type de pointeur de la fonction membre.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un wrapper d’appel simple `cw`, avec un type de résultat faible, telles que l’expression `cw(t, a2, ..., aN)` est identique à `INVOKE(pm, t, a2, ..., aN)`. Elle ne lève aucune exception.

Le wrapper d’appel retourné est dérivé `std::unary_function<cv Ty*, RTy>` (et de la définition du type imbriqué `result_type` comme synonyme de *RTy* et le type imbriqué `argument_type` comme synonyme de `cv Ty*`) uniquement si le type *Ty*  est un pointeur vers fonction membre avec un qualificateur cv `cv` qui n’accepte aucun argument.

Le wrapper d’appel retourné est dérivé `std::binary_function<cv Ty*, T2, RTy>` (et de la définition du type imbriqué `result_type` comme synonyme de *RTy*, le type imbriqué `first argument_type` comme synonyme de `cv Ty*`et le type imbriqué `second argument_type` comme un synonyme `T2`) uniquement si le type *Ty* est un pointeur vers fonction membre avec un qualificateur cv `cv` qui prend un argument de type `T2`.

### <a name="example"></a>Exemples

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }
```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a> mem_fun

Fonctions de modèle d’assistance utilisées pour construire des adaptateurs d’objets de fonction pour des fonctions membres en cas d’initialisation avec des arguments de pointeur. Dépréciées dans C ++ 11 pour [mem_fn](#mem_fn) et [lier](#bind)et supprimée dans C ++ 17.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>Paramètres

*pMem*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

### <a name="return-value"></a>Valeur de retour

Objet de fonction **const** ou **non_const** de type `mem_fun_t` ou `mem_fun1_t`.

### <a name="example"></a>Exemples

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a> mem_fun_ref

Fonctions de modèle d’assistance utilisées pour construire des adaptateurs d’objet de fonction pour des fonctions membres en cas d’initialisation avec des arguments de référence. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>Paramètres

*pMem*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

### <a name="return-value"></a>Valeur de retour

Un **const** ou `non_const` objet de fonction de type `mem_fun_ref_t` ou `mem_fun1_ref_t`.

### <a name="example"></a>Exemple

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a> not1

Retourne le complément d’un prédicat unaire. Déprécié pour [not_fn](#not_fn) dans C ++ 17.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>Paramètres

*prédicat*\
Prédicat unaire à rendre négatif.

### <a name="return-value"></a>Valeur de retour

Prédicat unaire qui est la négation du prédicat unaire modifié.

### <a name="remarks"></a>Notes

Si un `unary_negate` est construite à partir d’un prédicat unaire `predicate(x)`, il retourne `!predicate(x)`.

### <a name="example"></a>Exemple

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a> not2

Retourne le complément d’un prédicat binaire. Déprécié pour [not_fn](#not_fn) dans C ++ 17.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Paramètres

*Func*\
Prédicat binaire à rendre négatif.

### <a name="return-value"></a>Valeur de retour

Prédicat binaire qui est la négation du prédicat binaire modifié.

### <a name="remarks"></a>Notes

Si un `binary_negate` est construite à partir d’un prédicat binaire `binary_predicate(x, y)`, il retourne `!binary_predicate(x, y)`.

### <a name="example"></a>Exemple

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="not_fn"></a> not_fn

Le `not_fn` modèle de fonction prend un objet pouvant être appelé et retourne un objet pouvant être appelé. Lorsque l’objet pouvant être retourné est appelée ultérieurement avec des arguments, il les transmet à l’objet d’origine pouvant être appelé et logiquement inverse le résultat. Il conserve le comportement const de catégorie en qualification et la valeur de l’objet encapsulé pouvant être appelé. `not_fn` est une nouveauté dans C ++ 17 et remplace déconseillées `std::not1`, `std::not2`, `std::unary_negate`, et `std::binary_negate`.

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>Paramètres

*Func*\
Un objet pouvant être appelé utilisé pour construire l’appel de transfert wrapper.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un wrapper d’appel comme `return call_wrapper(std::forward<Callable>(func))`, en fonction de cette classe de démonstration uniquement :

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

Le constructeur explicite sur l’objet pouvant être *func* nécessite type `std::decay_t<Callable>` satisfaire les exigences de `MoveConstructible`, et `is_constructible_v<FD, Callable>` doivent être remplies. Il initialise l’objet encapsulé pouvant être appelé `fd` de `std::forward<Callable>(func)`et lève une exception levée par la construction de `fd`.

Le wrapper expose des opérateurs d’appel distingués par catégorie de référence lvalue ou rvalue et const qualification comme indiqué ici :

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

Les deux premiers sont les mêmes que `return !std::invoke(fd, std::forward<Args>(args)...)`. Les deux sont les mêmes que `return !std::invoke(std::move(fd), std::forward<Args>(args)...)`.

### <a name="example"></a>Exemple

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a> ptr_fun

Fonctions de modèle d’assistance utilisées pour convertir des pointeurs de fonction unaires et binaires, respectivement, en fonctions adaptables unaires et binaires. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Paramètres

*pfunc*\
Pointeur de fonction unaire ou binaire à convertir en fonction adaptable.

### <a name="return-value"></a>Valeur de retour

La première fonction de modèle retourne la fonction unaire [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) <`Arg`, **résultat**> (\* `pfunc`).

La deuxième fonction de modèle retourne la fonction binaire [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **résultat**> (\* `pfunc`).

### <a name="remarks"></a>Notes

Un pointeur de fonction est un objet de fonction. Il peut être passé à n’importe quel algorithme qui attend une fonction en tant que paramètre, mais il n’est pas adaptable. Informations sur ses types imbriqués sont requises à utiliser avec un adaptateur, par exemple, pour lier une valeur lui ou à rendre négative il. La conversion de pointeurs de fonction unaire et binaire par la fonction d’assistance `ptr_fun` permet aux adaptateurs de fonction d’utiliser des pointeurs de fonction unaire et binaire.

### <a name="example"></a>Exemple

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a> ref

Construit un `reference_wrapper` à partir d'un argument.

```cpp
template <class Ty>
    reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
    reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Valeur de retour

Une référence à `arg`; spécifiquement, `reference_wrapper<Ty>(arg)`.

### <a name="example"></a>Exemple

L’exemple suivant définit deux fonctions : une liée  à une variable chaîne, l’autre liée à une référence de la variable chaîne calculée par un appel à `ref`. Quand la valeur de la variable change, la première fonction continue à utiliser l’ancienne valeur et la seconde fonction utilise la nouvelle valeur.

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a> échange

Échange deux objets `function`.

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>Paramètres

*FT*\
Type contrôlé par les objets de fonction.

*F1*\
Premier objet de fonction.

*F2*\
Deuxième objet de fonction.

### <a name="remarks"></a>Notes

La fonction retourne `f1.swap(f2)`.

### <a name="example"></a>Exemple

```cpp
// std__functional__swap.cpp
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

    swap(fn0, fn1);
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
