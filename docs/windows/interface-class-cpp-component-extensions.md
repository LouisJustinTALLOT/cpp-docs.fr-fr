---
title: interface de classe (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- interface_CPP
dev_langs:
- C++
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74b4ea6b82de65f691d5d0350e161725625e4e1f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604484"
---
# <a name="interface-class--c-component-extensions"></a>classe d'interface  (extensions du composant C++)
Déclare une interface.  Pour plus d’informations sur les interfaces natives, consultez [__interface](../cpp/interface.md).  
  
## <a name="all-runtimes"></a>Tous les runtimes  

### <a name="syntax"></a>Syntaxe  
  
```  
interface_access  
interface class  
 name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};  
```  
  
### <a name="parameters"></a>Paramètres  
  
 *interface_access*  
 L’accessibilité d’une interface en dehors de l’assembly.  Les valeurs possibles sont **public** et **privé**.  **privé** est la valeur par défaut. Les interfaces imbriquées ne peut pas avoir un *interface_access* spécificateur.  
  
 *name*  
 Nom de l’interface.  
  
 *hériter_accès*  
 L’accessibilité de *base_interface*.  Le seul autorisé d’accessibilité pour une interface de base est **public** (la valeur par défaut).  
  
 *base_interface* (facultatif)  
 Une interface de base pour interface *nom*.  
  
### <a name="remarks"></a>Notes  
  
 **interface struct** équivaut à **classe d’interface**.  
  
 Une interface peut contenir les déclarations de fonctions, les événements et les propriétés.  Tous les membres d’interface ont une accessibilité publique. Une interface peut également contenir des propriétés, les fonctions, les événements et les données membres statiques, et ces membres statiques doivent être définies dans l’interface.  
  
 Une interface définit comment une classe peut être implémentée. Une interface n’est pas une classe et classes peuvent uniquement implémenter les interfaces. Lorsqu’une classe définit une fonction déclarée dans une interface, la fonction est implémentée, ne pas remplacé. Par conséquent, la recherche de nom n’inclut pas les membres d’interface.  
  
 Une classe ou un struct qui dérive d’une interface doit implémenter tous les membres de l’interface. Lors de l’implémentation d’interface *nom* vous devez également implémenter les interfaces dans le `base_interface` liste.  
  
 Pour plus d'informations, voir :  
  
-   [Constructeur d’interface statique](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [Interfaces génériques (Visual C++)](../windows/generic-interfaces-visual-cpp.md)  
  
 Pour plus d’informations sur les autres types CLR, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Vous pouvez détecter au moment de la compilation si un type est une interface avec `__is_interface_class(type)`. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Dans l’environnement de développement, vous pouvez obtenir la touche F1 sur ces mots clés en surbrillance le mot clé, (`interface class`, par exemple) et en appuyant sur F1.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 **Remarques**  
  
 (Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : `/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Remarques**  
  
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
  
 **Sortie**  
  
```Output  
in Function_3  
  
in Function_2  
  
in Function_1  
  
8  
  
OnClick: 7, 3.14159  
  
in Function_1  
```  
  
 L’exemple de code suivant montre deux façons d’implémenter des fonctions avec la même signature que déclarée dans plusieurs interfaces et où ces interfaces sont utilisées par une classe.  
  
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
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)