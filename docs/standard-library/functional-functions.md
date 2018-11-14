---
title: '&lt;functional&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
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
ms.openlocfilehash: cd89386ff421c199705856b9cf5f6b58ff25f7f5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519696"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt;, fonctions

||||
|-|-|-|
|[bind](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|
|[swap](#swap)|

## <a name="bind"></a>  bind

Lie des arguments à un objet pouvant être appelé.

```cpp
template <class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Paramètres

*Fty*<br/>
Type de l’objet à appeler.

*TN*<br/>
Type du N-ième argument de l’appel.

*fn*<br/>
Objet à appeler.

*tN*<br/>
N-ième argument de l’appel.

### <a name="remarks"></a>Notes

Les types `Fty, T1, T2, ..., TN` doivent être constructibles par copie et `INVOKE(fn, t1, ..., tN)` doit être une expression valide pour certaines valeurs `w1, w2, ..., wN`.

La première fonction de modèle retourne un wrapper d’appel de transfert `g` avec un type de résultat faible. L’effet de `g(u1, u2, ..., uM)` est `INVOKE(f, v1, v2, ..., vN, ` [result_of](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, où `cv` désigne les qualificateurs cv de `g` et les valeurs et les types des arguments liés `v1, v2, ..., vN` sont déterminées en tant que spécifiées ci-dessous. Vous l’utilisez pour lier des arguments à un objet pouvant être appelé afin de créer un objet pouvant être appelé avec une liste d’arguments personnalisés.

La deuxième fonction de modèle retourne un wrapper d’appel de transfert `g` avec un type imbriqué `result_type` qui est un synonyme de `Ret`. L’effet de `g(u1, u2, ..., uM)` est `INVOKE(f, v1, v2, ..., vN, Ret)`, où `cv` désigne les qualificateurs cv de `g`, et les valeurs et types des arguments liés `v1, v2, ..., vN` sont déterminés comme indiqué ci-dessous. Vous l’utilisez pour lier des arguments à un objet pouvant être appelé afin de créer un objet pouvant être appelé avec une liste d’arguments personnalisés et un type de retour spécifié.

Les valeurs des arguments liés `v1, v2, ..., vN` et leurs types correspondants `V1, V2, ..., VN` dépendent du type de l’argument correspondant `ti` de type `Ti` dans l’appel à `bind` et des qualificateurs cv `cv` du wrapper d’appel `g` comme suit :

si `ti` est de type `reference_wrapper<T>`, l’argument `vi` est `ti.get()` et son type `Vi` est `T&` ;

Si la valeur de `std::is_bind_expression<Ti>::value` est **true** l’argument `vi` est `ti(u1, u2, ..., uM)` et son type `Vi` est `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

si la valeur `j` de `std::is_placeholder<Ti>::value` n’est pas égale à zéro, l’argument `vi` est `uj` et son type `Vi` est `Uj&` ;

sinon l’argument `vi` est `ti` et son type `Vi` est `Ti` `cv` `&`.

Par exemple, avec une fonction `f(int, int)`, l’expression `bind(f, _1, 0)` retourne un wrappel d’appel de transfert `cw` de sorte que `cw(x)` appelle `f(x, 0)`. L’expression `bind(f, 0, _1)` retourne un wrapper d’appel de transfert `cw` de sorte que `cw(x)` appelle `f(0, x)`.

Le nombre d’arguments dans un appel à `bind` en plus de l’argument `fn` doit être égal au nombre d’arguments qui peut être passé à l’objet pouvant être appelé `fn`. Par conséquent, `bind(cos, 1.0)` est correct, et `bind(cos)` et `bind(cos, _1, 0.0)` sont incorrects.

Le nombre d’arguments dans l’appel de la fonction au wrapper d’appel retourné par `bind` doit être au moins aussi grand que la valeur numérotée la plus élevée de `is_placeholder<PH>::value` pour tous les arguments d’espace réservé dans l’appel à `bind`. Par conséquent, `bind(cos, _2)(0.0, 1.0)` est correct (et retourne `cos(1.0)`) et `bind(cos, _2)(0.0)` est incorrect.

### <a name="example"></a>Exemple

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

## <a name="bind1st"></a>  bind1st

Classe de modèle d’assistance qui crée un adaptateur pour convertir un objet de fonction binaire en objet de fonction unaire en liant le premier argument de la fonction binaire à une valeur spécifiée.

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Paramètres

*func*<br/>
Objet de fonction binaire à convertir en un objet de fonction unaire.

*left*<br/>
Valeur à laquelle le premier argument de l’objet de fonction binaire doit être lié.

### <a name="return-value"></a>Valeur de retour

L’objet de fonction unaire qui résulte de la liaison du premier argument de l’objet de fonction binaire à la valeur *gauche*.

### <a name="remarks"></a>Notes

Les binders de fonction sont un type d’adaptateur de fonction. Comme elles retournent des objets de fonction, elles peuvent être utilisées dans certains types de composition de fonction pour construire des expressions plus complexes et plus puissantes.

Si *func* est un objet de type `Operation` et `c` est une constante, puis `bind1st` ( `func`, `c`) est équivalente à la [binder1st](../standard-library/binder1st-class.md) constructeur de classe `binder1st` <  `Operation`> ( `func`, `c`) et est plus pratique.

### <a name="example"></a>Exemple

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

## <a name="bind2nd"></a>  bind2nd

Classe de modèle d’assistance qui crée un adaptateur pour convertir un objet de fonction binaire en objet de fonction unaire en liant le second argument de la fonction binaire à une valeur spécifiée.

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Paramètres

*func*<br/>
Objet de fonction binaire à convertir en un objet de fonction unaire.

*right*<br/>
Valeur à laquelle le deuxième argument de l’objet de fonction binaire doit être lié.

### <a name="return-value"></a>Valeur de retour

L’objet de fonction unaire qui résulte de la liaison le deuxième argument de l’objet de fonction binaire à la valeur *droit*.

### <a name="remarks"></a>Notes

Les binders de fonction sont un type d’adaptateur de fonction. Comme elles retournent des objets de fonction, elles peuvent être utilisées dans certains types de composition de fonction pour construire des expressions plus complexes et plus puissantes.

Si *func* est un objet de type `Operation` et `c` est une constante, puis `bind2nd` ( `func`, `c` ) est équivalente à la [binder2nd](../standard-library/binder2nd-class.md) constructeur de classe **binder2nd\<opération >** ( `func`, `c` ) et plus pratique.

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

## <a name="bit_and"></a>  bit_and

Objet de fonction prédéfini qui effectue l’opération AND au niveau du bit (`operator&` binaire) sur ses arguments.

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

*Type*, *T*, *U* n’importe quel type qui prend en charge un `operator&` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*<br/>
Opérande gauche de l’opération AND au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Droite*<br/>
Opérande droit de l’opération AND au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left & Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator&`.

### <a name="remarks"></a>Notes

Le foncteur `bit_and` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator&` binaire.

## <a name="bit_not"></a>  bit_not

Objet de fonction prédéfini qui effectue l’opération de complément (NOT) au niveau du bit (`operator~` unaire) sur ses arguments.

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
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*<br/>
Type prenant en charge un `operator~` unaire.

*Droite*<br/>
Opérande de l’opération de complément au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert d’un argument de référence lvalue ou rvalue du type inféré parfait *Type*.

### <a name="return-value"></a>Valeur de retour

Résultat de `~ Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator~`.

### <a name="remarks"></a>Notes

Le foncteur `bit_not` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator~` binaire.

## <a name="bit_or"></a>  bit_or

Objet de fonction prédéfini qui effectue l’opération OR au niveau du bit (`operator|`) sur ses arguments.

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
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U* n’importe quel type qui prend en charge un `operator|` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*<br/>
Opérande gauche de l’opération OR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Droite*<br/>
Opérande droit de l’opération OR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left | Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator|`.

### <a name="remarks"></a>Notes

Le foncteur `bit_or` est limité aux types intégraux pour les types de données de base ou aux types définis par l'utilisateur qui implémentent `operator|`.

## <a name="bit_xor"></a>  bit_xor

Objet de fonction prédéfini qui effectue l’opération XOR au niveau du bit (`operator^` binaire) sur ses arguments.

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

*Type*, *T*, *U* n’importe quel type qui prend en charge un `operator^` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*<br/>
Opérande gauche de l’opération XOR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Droite*<br/>
Opérande droit de l’opération XOR au niveau du bit. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

### <a name="return-value"></a>Valeur de retour

Résultat de `Left ^ Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator^`.

### <a name="remarks"></a>Notes

Le foncteur `bit_xor` est limité aux types intégraux pour les types de données de base ou aux types définis par l’utilisateur qui implémentent `operator^` binaire.

## <a name="cref"></a>  cref

Construit un `reference_wrapper` const à partir d'un argument.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type de l’argument à inclure dans un wrapper.

*arg*<br/>
Argument à inclure dans un wrapper.

### <a name="remarks"></a>Notes

La première fonction retourne `reference_wrapper<const Ty>(arg.get())`. Vous l’utilisez pour inclure une référence const dans un wrapper. La deuxième fonction retourne `reference_wrapper<const Ty>(arg)`. Vous l’utilisez pour inclure dans un wrapper une référence déjà incluse dans un wrapper comme référence const.

### <a name="example"></a>Exemple

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

## <a name="mem_fn"></a>  mem_fn

Génère un wrapper d'appel simple.

```cpp
template <class Ret, class Ty>
unspecified mem_fn(Ret Ty::*pm);
```

### <a name="parameters"></a>Paramètres

*RET*<br/>
Type de retour de la fonction incluse dans un wrapper.

*Ty*<br/>
Type de pointeur de la fonction membre.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un wrapper d’appel simple `cw` avec un type de résultat faible, de sorte que l’expression `cw(t, a2, ..., aN)` équivaut à `INVOKE(pm, t, a2, ..., aN)`. Elle ne lève aucune exception.

Le wrapper d’appel retourné est dérivé `std::unary_function<cv Ty*, Ret>` (d'où la définition du type imbriqué `result_type` comme synonyme de *Ret* et le type imbriqué `argument_type` comme synonyme de `cv Ty*`) uniquement si le type  *Ty* est un pointeur vers fonction membre avec un qualificateur cv `cv` qui n’accepte aucun argument.

Le wrapper d’appel retourné est dérivé `std::binary_function<cv Ty*, T2, Ret>` (d'où la définition du type imbriqué `result_type` comme synonyme de *Ret*, le type imbriqué `first argument_type` comme synonyme de `cv Ty*`et le type imbriqué `second argument_type`comme synonyme de `T2`) uniquement si le type *Ty* est un pointeur vers fonction membre avec un qualificateur cv `cv` qui prend un argument de type `T2`.

### <a name="example"></a>Exemple

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

## <a name="mem_fun"></a>  mem_fun

Fonctions de modèle d’assistance utilisées pour construire des adaptateurs d’objets de fonction pour des fonctions membres en cas d’initialisation avec des arguments de pointeur.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```

### <a name="parameters"></a>Paramètres

*pMem*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

### <a name="return-value"></a>Valeur de retour

Objet de fonction **const** ou **non_const** de type `mem_fun_t` ou `mem_fun1_t`.

### <a name="example"></a>Exemple

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

## <a name="mem_fun_ref"></a>  mem_fun_ref

Fonctions de modèle d’assistance utilisées pour construire des adaptateurs d’objet de fonction pour des fonctions membres en cas d’initialisation avec des arguments de référence.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```

### <a name="parameters"></a>Paramètres

*pMem*<br/>
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

## <a name="not1"></a>  not1

Retourne le complément d’un prédicat unaire.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```

### <a name="parameters"></a>Paramètres

*Pred*<br/>
Prédicat unaire à rendre négatif.

### <a name="return-value"></a>Valeur de retour

Prédicat unaire qui est la négation du prédicat unaire modifié.

### <a name="remarks"></a>Notes

Si un `unary_negate` est construit à partir d’un prédicat unaire **Pred**( *x*), il retourne **!Pred**( *x*).

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

## <a name="not2"></a>  not2

Retourne le complément d’un prédicat binaire.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Paramètres

*func*<br/>
Prédicat binaire à rendre négatif.

### <a name="return-value"></a>Valeur de retour

Prédicat binaire qui est la négation du prédicat binaire modifié.

### <a name="remarks"></a>Notes

Si un `binary_negate` est construit à partir d’un prédicat binaire **BinPred**( *x*), *y*), il retourne ! **BinPred**( *x*, *y*).

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

## <a name="ptr_fun"></a>  ptr_fun

Fonctions de modèle d’assistance utilisées pour convertir des pointeurs de fonction unaires et binaires, respectivement, en fonctions adaptables unaires et binaires.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Paramètres

*pfunc*<br/>
Pointeur de fonction unaire ou binaire à convertir en fonction adaptable.

### <a name="return-value"></a>Valeur de retour

La première fonction de modèle retourne la fonction unaire [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **résultat**> (\* `pfunc`).

La deuxième fonction de modèle retourne la fonction binaire [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **résultat**> (\* `pfunc`).

### <a name="remarks"></a>Notes

Un pointeur de fonction est un objet de fonction. Il peut être passé à n’importe quel algorithme de bibliothèque C++ Standard qui attend une fonction comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, en le liant à une valeur ou en l’utilisant avec une négation, vous devez également fournir les types imbriqués qui rendent l’adaptation possible. La conversion de pointeurs de fonction unaire et binaire par la fonction d’assistance `ptr_fun` permet aux adaptateurs de fonction d’utiliser des pointeurs de fonction unaire et binaire.

### <a name="example"></a>Exemple

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>  ref

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

## <a name="swap"></a>  swap

Échange deux objets `function`.

```cpp
template <class Fty>
void swap(function<Fty>& f1, function<Fty>& f2);
```

### <a name="parameters"></a>Paramètres

*Fty*<br/>
Type contrôlé par les objets de fonction.

*F1*<br/>
Premier objet de fonction.

*F2*<br/>
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

## <a name="see-also"></a>Voir aussi

[\<functional>](../standard-library/functional.md)<br/>
