---
description: 'En savoir plus sur : classe auto_handle'
title: auto_handle, classe
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::auto_handle::auto_handle
- msclr::auto_handle::get
- msclr::auto_handle::release
- msclr::auto_handle::reset
- msclr::auto_handle::swap
- msclr::auto_handle::operator->
- msclr::auto_handle::operator=
- msclr::auto_handle::operator auto_handle
- msclr::auto_handle::operator!
helpviewer_keywords:
- msclr::auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
ms.openlocfilehash: 9ac93d6b141f24a430aceb97f82fc90046622866
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282651"
---
# <a name="auto_handle-class"></a>auto_handle, classe

Gestion automatique des ressources, qui peut être utilisée pour incorporer un handle virtuel dans un type managé.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _element_type>
ref class auto_handle;
```

### <a name="parameters"></a>Paramètres

*_element_type*<br/>
Type managé à incorporer.

## <a name="members"></a><a name="members"></a> Membres

### <a name="public-constructors"></a>Constructeurs publics  

|Nom|Description|  
|---------|-----------|  
|[auto_handle::auto_handle](#auto-handle)|Constructeur `auto_handle`.|  
|[auto_handle :: ~ auto_handle](#tilde-auto-handle)|`auto_handle`Destructeur.|  

### <a name="public-methods"></a>Méthodes publiques  

|Nom|Description|  
|---------|-----------|  
|[auto_handle::get](#get)|Obtient l’objet contenu.|  
|[auto_handle::release](#release)|Libère l’objet de la `auto_handle` gestion.|
|[auto_handle::reset](#reset)|Détruisez l’objet détenu en cours et éventuellement la possession d’un nouvel objet.|
|[auto_handle::swap](#swap)|Échange des objets avec un autre `auto_handle` .|  

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|  
|---------|-----------|
|[auto_handle :: Operator-&gt;](#operator-arrow)|Opérateur d’accès aux membres.|
|[auto_handle::operator=](#operator-assign)|Opérateur d'assignation.|
|[auto_handle::operator auto_handle](#operator-auto-handle)|Opérateur de cast de type entre `auto_handle` les types et compatibles.|  
|[auto_handle::operator bool](#operator-bool)|Opérateur à utiliser `auto_handle` dans une expression conditionnelle.|
|[auto_handle :: Operator !](#operator-logical-not)|Opérateur à utiliser `auto_handle` dans une expression conditionnelle.|  

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr\auto_handle.h>

**Espace de noms** msclr,

## <a name="auto_handleauto_handle"></a><a name="auto-handle"></a> auto_handle :: auto_handle

Constructeur `auto_handle`.

```cpp
auto_handle();
auto_handle(
   _element_type ^ _ptr
);
auto_handle(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>Paramètres

*_ptr*<br/>
Objet à posséder.

*_right*<br/>
`auto_handle` existant.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_auto_handle.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;
ref class RefClassA {
protected:
   String^ m_s;
public:
   RefClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in RefClassA constructor: " + m_s );
   }
   ~RefClassA() {
      Console::WriteLine( "in RefClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class RefClassB : RefClassA {
public:
   RefClassB( String^ s ) : RefClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   {
      auto_handle<RefClassA> a(gcnew RefClassA( "first" ) );
      a->PrintHello();
   }

   {
      auto_handle<RefClassB> b(gcnew RefClassB( "second" ) );
      b->PrintHello();
      auto_handle<RefClassA> a(b); //construct from derived type
      a->PrintHello();
      auto_handle<RefClassA> a2(a); //construct from same type
      a2->PrintHello();
   }

   Console::WriteLine("done");
}
```

```Output
in RefClassA constructor: first
Hello from first A!
in RefClassA destructor: first
in RefClassA constructor: second
Hello from second B!
Hello from second A!
Hello from second A!
in RefClassA destructor: second
done
```

## <a name="auto_handleauto_handle"></a><a name="tilde-auto-handle"></a> auto_handle :: ~ auto_handle

`auto_handle`Destructeur.

```cpp
~auto_handle();
```

### <a name="remarks"></a>Notes

Le destructeur détruit également l’objet détenu.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_dtor.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;

ref class ClassA {
public:
   ClassA() { Console::WriteLine( "ClassA constructor" ); }
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }
};

int main()
{
   // create a new scope for a:
   {
      auto_handle<ClassA> a = gcnew ClassA;
   }
   // a goes out of scope here, invoking its destructor
   // which in turns destructs the ClassA object.

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor
ClassA destructor
done
```

## <a name="auto_handleget"></a><a name="get"></a> auto_handle :: obtient

Obtient l’objet contenu.

```cpp
_element_type ^ get();
```

### <a name="return-value"></a>Valeur retournée

Objet contenu.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_get.cpp
// compile with: /clr
#include "msclr\auto_handle.h"

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ){
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

void PrintA( ClassA^ a ) {
   a->PrintHello();
}

int main() {
   auto_handle<ClassA> a = gcnew ClassA( "first" );
   a->PrintHello();

   ClassA^ a2 = a.get();
   a2->PrintHello();

   PrintA( a.get() );
}
```

```Output
in ClassA constructor:first
Hello from first A!
Hello from first A!
Hello from first A!
in ClassA destructor:first
```

## <a name="auto_handlerelease"></a><a name="release"></a> auto_handle :: Release

Libère l’objet de la `auto_handle` gestion.

```cpp
_element_type ^ release();
```

### <a name="return-value"></a>Valeur retournée

Objet libéré.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_release.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   ClassA^ a;

   // create a new scope:
   {
      auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
      auto_handle<ClassA> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="auto_handlereset"></a><a name="reset"></a> auto_handle :: Reset

Détruisez l’objet détenu en cours et éventuellement la possession d’un nouvel objet.

```cpp
void reset(
   _element_type ^ _new_ptr
);
void reset();
```

### <a name="parameters"></a>Paramètres

*_new_ptr*<br/>
Facultatif Nouvel objet.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_reset.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   auto_handle<ClassA> agc1 = gcnew ClassA( "first" );
   agc1->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   agc1.reset( ha ); // release first object, reference second
   agc1->PrintHello();

   agc1.reset(); // release second object, set to nullptr

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
Hello from first A!
ClassA constructor: second
ClassA destructor: first
Hello from second A!
ClassA destructor: second
done
```

## <a name="auto_handleswap"></a><a name="swap"></a> auto_handle :: swap

Échange des objets avec un autre `auto_handle` .

```cpp
void swap(
   auto_handle<_element_type> % _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
`auto_handle`Avec lequel échanger des objets.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_swap.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   s1.swap( s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="auto_handleoperator-gt"></a><a name="operator-arrow"></a> auto_handle :: Operator-&gt;

Opérateur d’accès aux membres.

```cpp
_element_type ^ operator->();
```

### <a name="return-value"></a>Valeur retournée

Objet encapsulé par `auto_handle` .

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_op_arrow.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }

   int m_i;
};

int main() {
   auto_handle<ClassA> a( gcnew ClassA( "first" ) );
   a->PrintHello();

   a->m_i = 5;
   Console::WriteLine( "a->m_i = {0}", a->m_i );
}
```

```Output
Hello from first A!
a->m_i = 5
```

## <a name="auto_handleoperator"></a><a name="operator-assign"></a> auto_handle :: Operator =

Opérateur d'assignation.

```cpp
auto_handle<_element_type> % operator=(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle<_element_type> % operator=(
   auto_handle<_other_type> % _right
);
```

### <a name="parameters"></a>Paramètres

*_right*<br/>
`auto_handle`À assigner au actuel `auto_handle` .

### <a name="return-value"></a>Valeur retournée

Actuel `auto_handle` , à présent propriétaire `_right` .

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_op_assign.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String^ s ) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   auto_handle<ClassA> a;
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   auto_handle<ClassB> b(gcnew ClassB( "second" ) );
   b->PrintHello();
   a = b; // assign from derived type
   a->PrintHello();

   Console::WriteLine("done");
}
```

```Output
in ClassA constructor: first
Hello from first A!
in ClassA constructor: second
Hello from second B!
in ClassA destructor: first
Hello from second A!
done
in ClassA destructor: second
```

## <a name="auto_handleoperator-auto_handle"></a><a name="operator-auto-handle"></a> auto_handle :: Operator auto_handle

Opérateur de cast de type entre `auto_handle` les types et compatibles.

```cpp
template<typename _other_type>
operator auto_handle<_other_type>();
```

### <a name="return-value"></a>Valeur retournée

Cast actuel en `auto_handle` `auto_handle<_other_type>` .

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_op_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {}

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_handle<ClassB> b = gcnew ClassB("first");
   b->PrintHello();
   auto_handle<ClassA> a = (auto_handle<ClassA>)b;
   a->PrintHello();
}
```

```Output
Hello from first B!
Hello from first A!
```

## <a name="auto_handleoperator-bool"></a><a name="operator-bool"></a> auto_handle :: operator bool

Opérateur à utiliser `auto_handle` dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur retournée

**`true`** Si l’objet encapsulé est valide ; **`false`** sinon,.

### <a name="remarks"></a>Notes

Cet opérateur convertit en fait `_detail_class::_safe_bool` la valeur qui est plus sûre que **`bool`** parce qu’il ne peut pas être converti en type intégral.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="auto_handleoperator"></a><a name="operator-logical-not"></a> auto_handle :: Operator !

Opérateur à utiliser `auto_handle` dans une expression conditionnelle.

```cpp
bool operator!();
```

### <a name="return-value"></a>Valeur retournée

**`true`** Si l’objet encapsulé n’est pas valide ; **`false`** sinon,.

### <a name="example"></a>Exemple

```cpp
// msl_auto_handle_operator_not.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "something";
   if ( s1) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```
