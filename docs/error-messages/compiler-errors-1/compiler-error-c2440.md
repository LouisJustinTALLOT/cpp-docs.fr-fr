---
title: Erreur du compilateur C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 74c5032338b3f4cf30bdb75bdf070cee7b67ce58
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742110"
---
# <a name="compiler-error-c2440"></a>Erreur du compilateur C2440

'conversion' : impossible de convertir de’type1 'en’type2 '

Le compilateur ne peut pas effectuer un cast de `type1` en `type2` .

L’erreur C2440 peut être provoquée si vous tentez d’initialiser un non const **`char*`** (ou `wchar_t*` ) à l’aide d’un littéral de chaîne dans du code C++, lorsque l’option de conformité du compilateur [/Zc : strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) est définie. En C, le type d’un littéral de chaîne est un tableau de **`char`** , mais en C++, il s’agit d’un tableau de `const char` .

## <a name="examples"></a>Exemples

Cet exemple génère l’C2440 :

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

L’C2440 peut également être provoquée si vous tentez de convertir un pointeur en membre en void *. L’exemple suivant génère l’C2440 :

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

L’exception C2440 peut également être provoquée si vous tentez d’effectuer un cast à partir d’un type qui est uniquement en avant déclaré mais pas défini. Cet exemple génère l’C2440 :

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

Les erreurs C2440 sur les lignes 15 et 16 de l’exemple suivant sont qualifiées avec le `Incompatible calling conventions for UDT return value` message. Un *UDT* est un type défini par l’utilisateur, tel qu’une classe, un struct ou une Union. Ces types d’erreurs d’incompatibilité sont dus au fait que la Convention d’appel d’un UDT spécifié dans le type de retour d’une déclaration anticipée est en conflit avec la Convention d’appel réelle de l’UDT et lorsqu’un pointeur de fonction est impliqué.

Dans l’exemple, il existe d’abord des déclarations anticipées pour un struct et pour une fonction qui retourne la structure. le compilateur suppose que la structure utilise la Convention d’appel C++. Ensuite, la définition de la structure, qui, par défaut, utilise la Convention d’appel C. Étant donné que le compilateur ne connaît pas la Convention d’appel de la structure tant qu’il n’a pas terminé la lecture du struct entier, la Convention d’appel pour le struct dans le type de retour de `get_c2` est également supposée être en C++.

La structure est suivie d’une autre déclaration de fonction qui retourne la structure, mais à ce stade, le compilateur sait que la Convention d’appel du struct est C++. De même, le pointeur de fonction, qui retourne la structure, est défini après la définition de la structure, de sorte que le compilateur sait que la structure utilise la Convention d’appel C++.

Pour résoudre l’erreur C2440 qui se produit en raison de conventions d’appel incompatibles, déclarez les fonctions qui retournent un UDT après la définition de l’UDT.

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

L’C2440 peut également se produire si vous assignez zéro à un pointeur intérieur :

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

L’erreur C2440 peut également se produire pour une utilisation incorrecte d’une conversion définie par l’utilisateur. Par exemple, lorsqu’un opérateur de conversion a été défini en tant que **`explicit`** , le compilateur ne peut pas l’utiliser dans une conversion implicite. Pour plus d’informations sur les conversions définies par l’utilisateur, consultez [conversions définies par l’utilisateur (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). Cet exemple génère l’C2440 :

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

L’C2440 peut également se produire si vous essayez de créer une instance d’un tableau de Visual C++ dont le type est un <xref:System.Array> .  Pour plus d’informations, consultez [Tableaux](../../extensions/arrays-cpp-component-extensions.md).  L’exemple suivant génère l’C2440 :

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

L’option C2440 peut également se produire en raison de modifications apportées à la fonctionnalité attributs.  L’exemple suivant génère l’C2440.

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

Le compilateur Microsoft C++ n’autorise plus le cast de l' [opérateur const_cast](../../cpp/const-cast-operator.md) lorsque le code source qui utilise la programmation **/CLR** est compilé.

Pour résoudre ce C2440, utilisez l’opérateur de cast correct. Pour plus d’informations, consultez [casting Operators](../../cpp/casting-operators.md).

Cet exemple génère l’C2440 :

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

L’C2440 peut se produire en raison de modifications de conformité au compilateur dans Visual Studio 2015 Update 3. Auparavant, le compilateur traitait de manière incorrecte certaines expressions distinctes en tant que type identique lors de l’identification d’une correspondance de modèle pour une **`static_cast`** opération. À présent, le compilateur distingue correctement les types, et le code qui s’est appuyé sur le **`static_cast`** comportement précédent est rompu. Pour résoudre ce problème, modifiez l’argument de modèle pour qu’il corresponde au type de paramètre de modèle, ou utilisez un **`reinterpret_cast`** cast de style C ou.

Cet exemple génère l’C2440 :

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 et versions ultérieures déclenchent correctement les erreurs de compilateur liées à la création d’objets à l’aide de listes d’initialiseurs qui n’ont pas été interceptées dans Visual Studio 2015 et peuvent provoquer des blocages ou un comportement d’exécution non défini. En C++ 17, Copy-List-Initialize, le compilateur est tenu de prendre en compte un constructeur explicite pour la résolution de surcharge, mais doit déclencher une erreur si cette surcharge est réellement choisie.

L’exemple suivant compile dans Visual Studio 2015, mais pas dans Visual Studio 2017.

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

Pour corriger l’erreur, utilisez une initialisation directe :

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

### <a name="cv-qualifiers-in-class-construction"></a>Qualificateurs cv dans la construction de la classe

Dans Visual Studio 2015, le compilateur ignore parfois à tort le qualificateur cv pendant la génération d’un objet de classe par le biais d’un appel de constructeur. Cela peut provoquer un incident ou un comportement inattendu au moment de l’exécution. L’exemple suivant compile dans Visual Studio 2015, mais génère une erreur du compilateur dans Visual Studio 2017 et versions ultérieures :

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Pour corriger cette erreur, déclarez l’opérateur int() en tant que const.
