---
description: 'En savoir plus sur : Comment : utiliser safe_cast en C++/CLI'
title: 'Procédure : Utiliser safe_cast dans C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: f921371f97f967f9517121aaa163f79769781211
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145572"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>Procédure : Utiliser safe_cast dans C++/CLI

Cet article explique comment utiliser safe_cast dans les applications C++/CLI. Pour plus d’informations sur les safe_cast en C++/CX, consultez [safe_cast](../extensions/safe-cast-cpp-component-extensions.md).

## <a name="upcasting"></a>Un upcast

Un upcast est un cast d’un type dérivé vers l’une de ses classes de base. Ce cast est sécurisé et ne nécessite pas de notation de cast explicite. L’exemple suivant montre comment effectuer un upcast, avec `safe_cast` et sans celui-ci.

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Passer

Un downcast est un cast d’une classe de base en une classe dérivée de la classe de base.  Un cast aval est sécurisé uniquement si l’objet qui est adressé au moment de l’exécution est en fait un objet de classe dérivée.  Contrairement **`static_cast`** `safe_cast` à, effectue une vérification dynamique et lève une exception en <xref:System.InvalidCastException> cas d’échec de la conversion.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>safe_cast avec les conversions définies par l’utilisateur

L’exemple suivant montre comment vous pouvez utiliser `safe_cast` pour appeler des conversions définies par l’utilisateur.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>opérations de safe_cast et de boxing

### <a name="boxing"></a>Boxing

Le boxing est défini comme une conversion injectée par le compilateur, définie par l’utilisateur.  Par conséquent, vous pouvez utiliser `safe_cast` pour Box une valeur sur le tas CLR.

L’exemple suivant illustre le Boxing avec des types de valeur simples et définis par l’utilisateur.  Une `safe_cast` variable de type valeur qui se trouve sur la pile native, afin qu’elle puisse être assignée à une variable sur le tas récupéré par le garbage collector.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

L’exemple suivant montre que le boxing est prioritaire sur une conversion définie par l’utilisateur dans une `safe_cast` opération.

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Unboxing

L’unboxing est définie en tant que conversion injectée par le compilateur et définie par l’utilisateur.  Par conséquent, vous pouvez utiliser `safe_cast` pour unboxing une valeur sur le tas CLR.

L’unboxing est une conversion définie par l’utilisateur, mais contrairement au boxing, l’unboxing doit être explicite, autrement dit, elle doit être effectuée par un **`static_cast`** cast de style C ou, ou bien, l' `safe_cast` unboxing ne peut pas être effectué implicitement.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

L’exemple suivant illustre l’unboxing avec les types valeur et les types primitifs.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>types safe_cast et génériques

L’exemple suivant montre comment vous pouvez utiliser `safe_cast` pour effectuer un cast aval avec un type générique.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>Voir aussi

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
