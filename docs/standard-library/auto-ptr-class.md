---
title: auto_ptr, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
dev_langs:
- C++
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 945de6e2ef7e9ec3967091f88b1d0cfeaa8df5e3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108887"
---
# <a name="autoptr-class"></a>auto_ptr, classe

Encapsule un pointeur intelligent autour d’une ressource qui garantit que celle-ci est détruite automatiquement quand le contrôle quitte un bloc.

La classe `unique_ptr` plus performante remplace `auto_ptr`. Pour plus d’informations, consultez [unique_ptr, classe](../standard-library/unique-ptr-class.md).

Pour plus d’informations sur `throw()` et sur la gestion des exceptions, consultez [Spécifications d’exceptions (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class auto_ptr {
public:
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```
### <a name="parameters"></a>Paramètres

*right*<br/>
`auto_ptr` à partir duquel obtenir une ressource existante.

*ptr*<br/>
Pointeur spécifié pour remplacer le pointeur stocké.

## <a name="remarks"></a>Notes

La classe de modèle décrit un pointeur intelligent, appelé un `auto_ptr`, dans un objet alloué. Le pointeur doit avoir la valeur null ou désigner un objet alloué par **nouveau**. Le `auto_ptr` transfère la propriété si sa valeur stockée est assignée à un autre objet. (Il remplace la valeur stockée après un transfert avec un pointeur null.) Le destructeur de `auto_ptr<Type>` supprime l'objet alloué. Le `auto_ptr<Type>` garantit qu'un objet alloué est supprimé automatiquement quand le contrôle quitte un bloc, même suite à la levée d'une exception. Vous ne devez pas construire deux objets `auto_ptr<Type>` qui possèdent le même objet.

Vous pouvez passer un objet `auto_ptr<Type>` par valeur en tant qu'argument à un appel de fonction. Un `auto_ptr` ne peut pas être un élément d'un conteneur de bibliothèque STL. Vous ne pouvez pas gérer de manière fiable une séquence d’objets `auto_ptr<Type>` avec un conteneur de bibliothèque C++ Standard.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[auto_ptr](#auto_ptr)|Constructeur des objets de type `auto_ptr`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[element_type](#element_type)|Le type est un synonyme du paramètre de modèle `Type`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[get](#get)|La fonction membre retourne le pointeur stocké `myptr`.|
|[release](#release)|Le membre remplace le pointeur stocké `myptr` par un pointeur null et il retourne le pointeur stocké précédemment.|
|[reset](#reset)|La fonction membre évalue l'expression `delete myptr`, mais uniquement si la valeur de pointeur stocké `myptr` change suite à l'appel de fonction. Elle remplace ensuite le pointeur stocké par *ptr*.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Opérateur d'assignation qui transfère la propriété d'un objet `auto_ptr` à un autre.|
|[operator*](#op_star)|Opérateur de déréférencement pour les objets de type `auto_ptr`.|
|[operator->](#op_arrow)|Opérateur pour autoriser l'accès aux membres.|
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|Effectue un cast d'un type de `auto_ptr` vers un autre type de `auto_ptr`.|
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|Effectue un cast d'un `auto_ptr` vers un `auto_ptr_ref`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="auto_ptr"></a>  auto_ptr::auto_ptr

Constructeur des objets de type `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Pointeur vers l’objet que `auto_ptr` encapsule.

*right*<br/>
L’objet `auto_ptr` doit être copié par le constructeur.

### <a name="remarks"></a>Notes

Le premier constructeur stocke *ptr* dans `myptr`, le pointeur stocké vers l’objet alloué. Le deuxième constructeur transfère la propriété du pointeur stocké dans *droit*, en stockant *droit*. [mise en production](#release) dans `myptr`.

Le troisième constructeur comporte comme la seconde, à ceci près qu’il stocke `right`. `ref`. `release` dans `myptr`, où `ref` est la référence stockée dans `right`.

Le constructeur de modèle comporte comme le deuxième constructeur, à condition qu’un pointeur vers `Other` peut être implicitement converti en un pointeur vers `Type`.

### <a name="example"></a>Exemple

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

## <a name="element_type"></a>  auto_ptr::element_type

Le type est un synonyme du paramètre de modèle `Type`.

```cpp

typedef Type element  _type;
```

## <a name="get"></a>  auto_ptr::get

La fonction membre retourne le pointeur stocké `myptr`.

```cpp
Type *get() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le pointeur stocké `myptr`.

### <a name="example"></a>Exemple

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="op_eq"></a>  auto_ptr::operator=

Opérateur d'assignation qui transfère la propriété d'un objet `auto_ptr` à un autre.

```cpp
template <class Other>
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Objet de type `auto_ptr`.

### <a name="return-value"></a>Valeur de retour

Référence à un objet de type `auto_ptr`\< **Type**.

### <a name="remarks"></a>Notes

L’assignation évalue l’expression `delete myptr`, mais uniquement si le pointeur stocké `myptr` modifications suite à l’affectation. Elle transfère ensuite la propriété du pointeur stocké dans _ *Right* en stockant \_ *Right*. [mise en production](#release) dans `myptr`. La fonction retourne **\*this**.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l’opérateur membre, consultez [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_star"></a>  auto_ptr::operator*

Opérateur de déréférencement pour les objets de type `auto_ptr`.

```cpp
Type& operator*() const throw();
```

### <a name="return-value"></a>Valeur de retour

Une référence à un objet de type `Type` qui possède le pointeur.

### <a name="remarks"></a>Notes

L’opérateur d’indirection retourne `*`[get](#get). Par conséquent, le pointeur stocké ne doit pas être null.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la fonction membre, consultez [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_arrow"></a>  auto_ptr::operator-&gt;

Opérateur pour autoriser l'accès aux membres.

```cpp
Type * operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un membre de l’objet qui `auto_ptr` possède.

### <a name="remarks"></a>Notes

L’opérateur de sélection retourne [get](#get)`( )` de sorte que l’expression *ap*-> **member** se comporte comme (*ap*. **get**( ) )-> **member**, où *ap* est un objet de classe `auto_ptr`\< **Type**>. Par conséquent, le pointeur stocké ne doit pas être null, et `Type` doit être une classe, un struct ou un type d’union avec un `member` membre.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la fonction membre, consultez [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_auto_ptr_lt_other_gt"></a>  auto_ptr::operator auto_ptr&lt;Other&gt;

Effectue un cast d'un type de `auto_ptr` vers un autre type de `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

### <a name="return-value"></a>Valeur de retour

L’opérateur de cast de type retourne `auto_ptr` \< **Other**>(**\*this**).

### <a name="example"></a>Exemple

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

## <a name="op_auto_ptr_ref_lt_other_gt"></a>  auto_ptr::operator auto_ptr_ref&lt;Other&gt;

Effectue un cast d'un `auto_ptr` vers un `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

### <a name="return-value"></a>Valeur de retour

L’opérateur de cast de type retourne **auto_ptr_ref**\< **Other**>(**\*this**).

### <a name="example"></a>Exemple

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

## <a name="release"></a>  auto_ptr::release

Le membre remplace le pointeur stocké `myptr` par un pointeur null et il retourne le pointeur stocké précédemment.

```cpp
Type *release() throw();
```

### <a name="return-value"></a>Valeur de retour

Pointeur stocké précédemment.

### <a name="remarks"></a>Notes

Le membre remplace le pointeur stocké `myptr` par un pointeur null et il retourne le pointeur stocké précédemment.

### <a name="example"></a>Exemple

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="reset"></a>  auto_ptr::reset

La fonction membre évalue l’expression `delete myptr`, mais uniquement si la valeur de pointeur stocké `myptr` change à la suite d’un appel de fonction. Elle remplace ensuite le pointeur stocké par `ptr`.

```cpp
void reset(Type* ptr = 0);
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Le pointeur spécifié pour remplacer le pointeur stocké `myptr`.

### <a name="example"></a>Exemple

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[unique_ptr, classe](../standard-library/unique-ptr-class.md)<br/>
