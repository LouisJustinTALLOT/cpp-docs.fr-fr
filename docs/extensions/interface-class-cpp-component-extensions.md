---
title: classe d’interface (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: cb4566a0094db6d9e0cc97d81718a18a6df5cf18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172163"
---
# <a name="interface-class--ccli-and-ccx"></a>classe d’interface (C++/CLI et C++/CX)

Déclare une interface.  Pour plus d’informations sur les interfaces natives, consultez [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Paramètres

*interface_access*<br/>
L’accessibilité d’une interface en dehors de l’assembly.  Les valeurs possibles sont **public** et **private**.  **private** est la valeur par défaut. Les interfaces imbriquées ne peuvent pas disposer d’un spécificateur *interface_access*.

*name*<br/>
Nom de l’interface.

*inherit_access*<br/>
L’accessibilité de *base_interface*.  La seule accessibilité autorisée pour une interface de base est **public** (la valeur par défaut).

*base_interface*<br/>
(Facultatif) Interface de base pour le *nom* de l’interface.

### <a name="remarks"></a>Notes

**interface struct** équivaut à **interface class**.

Une interface peut contenir des déclarations de fonctions, d’événements et de propriétés.  Tous les membres d’interface disposent d’une accessibilité publique. Une interface peut également contenir des propriétés, des événements, des fonctions et des membres de données statiques. Ces membres statiques doivent être définis dans l’interface.

Une interface définit comment une classe peut être implémentée. Une interface n’est pas une classe et les classes peuvent uniquement implémenter des interfaces. Lorsqu’une classe définit une fonction déclarée dans une interface, la fonction est implémentée, et non pas remplacée. Par conséquent, la recherche de nom n’inclut pas les membres d’interface.

Une classe ou un struct qui dérivent d’une interface doivent implémenter tous les membres de l’interface. Lors de l’implémentation du *nom* de l’interface, vous devez également implémenter les interfaces dans la liste `base_interface`.

Pour plus d'informations, consultez les pages suivantes :

- [Constructeur d’interface statique](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Interfaces génériques (C++/CLI)](generic-interfaces-visual-cpp.md)

Pour plus d’informations sur les autres types CLR, consultez [Classes et structs](classes-and-structs-cpp-component-extensions.md).

Au moment de la compilation, vous pouvez détecter si un type est une interface avec `__is_interface_class(type)`. Pour plus d’informations, consultez [Compiler Support for Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md) (Prise en charge du compilateur pour les caractéristiques de type).

Dans l’environnement de développement, vous pouvez obtenir l’aide F1 pour ces mots clés en surlignant le mot clé (par exemple, `interface class`) et en appuyant sur F1.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Common Language Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre comment une interface peut définir le comportement d’une fonction d’horloge.

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

L’exemple de code suivant montre deux manières d’implémenter des fonctions avec la même signature déclarée dans plusieurs interfaces et dans l’emplacement dans lequel ces interfaces sont utilisées par une classe.

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
