---
description: 'En savoir plus sur : Comment : définir et utiliser des délégués (C++/CLI)'
title: 'Comment : définir et utiliser des délégués (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: 4229af2015db3a9a77722e9e4cc24b80aa05a49b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175753"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>Comment : définir et utiliser des délégués (C++/CLI)

Cet article explique comment définir et utiliser des délégués en C++/CLI.

Bien que le .NET Framework fournisse plusieurs délégués, vous pouvez parfois être amené à définir de nouveaux délégués.

L’exemple de code suivant définit un délégué nommé `MyCallback` . Le code de gestion d’événements — la fonction qui est appelée quand ce nouveau délégué est déclenché — doit avoir un type de retour **`void`** et prendre une <xref:System.String> référence.

La fonction main utilise une méthode statique définie par `SomeClass` pour instancier le `MyCallback` délégué. Le délégué devient alors une autre méthode d’appel à cette fonction, comme illustré par l’envoi de la chaîne « Single » à l’objet délégué. Ensuite, les instances supplémentaires de `MyCallback` sont liées ensemble, puis exécutées par un appel à l’objet délégué.

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

L’exemple de code suivant montre comment associer un délégué à un membre d’une classe value.

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>Comment composer des délégués

Vous pouvez utiliser l' `-` opérateur «» pour supprimer un délégué de composant d’un délégué composé.

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**Sortie**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>Passer un délégué ^ à une fonction native qui attend un pointeur de fonction

À partir d’un composant managé, vous pouvez appeler une fonction native avec des paramètres de pointeur de fonction où la fonction native peut ensuite appeler la fonction membre du délégué du composant managé.

Cet exemple crée le fichier. dll qui exporte la fonction native :

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

L’exemple suivant utilise le fichier. dll et passe un handle de délégué à la fonction native qui attend un pointeur de fonction.

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**Sortie**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>Pour associer des délégués à des fonctions non managées

Pour associer un délégué à une fonction native, vous devez encapsuler la fonction native dans un type managé et déclarer la fonction à appeler via `PInvoke` .

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**Sortie**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>Pour utiliser des délégués indépendants

Vous pouvez utiliser un délégué indépendant pour passer une instance du type dont vous souhaitez appeler la fonction lorsque le délégué est appelé.

Les délégués indépendants sont particulièrement utiles si vous souhaitez itérer au sein des objets d’une collection (à l’aide [de for each, dans](../dotnet/for-each-in.md) des mots clés) et appeler une fonction membre sur chaque instance.

Voici comment déclarer, instancier et appeler des délégués liés et indépendants :

|Action|Délégués liés|Délégués indépendants|
|------------|---------------------|-----------------------|
|Declare|La signature du délégué doit correspondre à la signature de la fonction que vous souhaitez appeler par le biais du délégué.|Le premier paramètre de la signature du délégué est le type de **`this`** pour l’objet que vous souhaitez appeler.<br /><br /> Après le premier paramètre, la signature du délégué doit correspondre à la signature de la fonction que vous souhaitez appeler par le biais du délégué.|
|Créées|Quand vous instanciez un délégué lié, vous pouvez spécifier une fonction d’instance, ou une fonction membre globale ou statique.<br /><br /> Pour spécifier une fonction d’instance, le premier paramètre est une instance du type dont vous souhaitez appeler la fonction et le deuxième paramètre est l’adresse de la fonction que vous souhaitez appeler.<br /><br /> Si vous souhaitez appeler une fonction membre globale ou statique, il vous suffit de transmettre le nom d’une fonction globale ou le nom de la fonction membre statique.|Quand vous instanciez un délégué indépendant, il vous suffit de transmettre l’adresse de la fonction que vous souhaitez appeler.|
|Call|Quand vous appelez un délégué lié, il vous suffit de passer les paramètres requis par la signature du délégué.|Identique à un délégué lié, mais n’oubliez pas que le premier paramètre doit être une instance de l’objet qui contient la fonction que vous souhaitez appeler.|

Cet exemple montre comment déclarer, instancier et appeler des délégués indépendants :

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**Sortie**

```Output
2
3
2
3
2
7
8
7
8
7
```

L’exemple suivant montre comment utiliser des délégués indépendants et le [pour chaque, dans](../dotnet/for-each-in.md) les mots clés pour itérer au sein des objets d’une collection et appeler une fonction membre sur chaque instance.

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

Cet exemple crée un délégué indépendant aux fonctions d’accesseur d’une propriété :

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**Sortie**

```Output
11
```

L’exemple suivant montre comment appeler un délégué multicast, où une instance est liée et qu’une instance est détachée.

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**Sortie**

```Output
in f(R ^ r)
in f()
```

L’exemple suivant montre comment créer et appeler un délégué générique indépendant.

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**Sortie**

```Output
12
14
```

## <a name="see-also"></a>Voir aussi

[delegate (extensions du composant C++)](../extensions/delegate-cpp-component-extensions.md)
