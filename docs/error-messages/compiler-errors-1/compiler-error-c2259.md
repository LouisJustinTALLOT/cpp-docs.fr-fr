---
title: Erreur du compilateur C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 403d674eae696eb42a837aef9d6e97c4b5b8f6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758786"
---
# <a name="compiler-error-c2259"></a>Erreur du compilateur C2259

'class' : impossible d’instancier une classe abstraite

Le code déclare une instance d’une classe ou d’une structure abstraite.

Vous ne pouvez pas instancier une classe ou une structure avec une ou plusieurs fonctions virtuelles pures. Pour instancier des objets d’une classe dérivée, la classe dérivée doit substituer chaque fonction virtuelle pure.

Pour plus d’informations, consultez [classes implicitement abstraites](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).

L’exemple suivant génère l’C2259 :

```cpp
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

Chaque fois que vous dérivez d’une interface et implémentez les méthodes d’interface dans la classe dérivée avec des autorisations d’accès autres que public, vous pouvez recevoir C2259.  Cela est dû au fait que le compilateur s’attend à ce que les méthodes d’interface implémentées dans la classe dérivée aient un accès public. Lorsque vous implémentez les fonctions membres pour une interface avec des autorisations d’accès plus restrictives, le compilateur ne les considère pas comme des implémentations pour les méthodes d’interface définies dans l’interface, qui à son tour fait de la classe dérivée une classe abstraite.

Il existe deux solutions possibles pour le problème :

- Rendez les autorisations d’accès publiques pour les méthodes implémentées.

- Utilisez l’opérateur de résolution de portée pour les méthodes d’interface implémentées dans la classe dérivée pour qualifier le nom de la méthode implémentée avec le nom de l’interface.

C2259 peut également se produire en raison du travail de conformité effectué dans Visual Studio 2005, **/Zc : wchar_t** est désormais activé par défaut. Dans ce cas, C2599 peut être résolu en compilant avec **/Zc : wchar_t-** , pour connaître le comportement des versions précédentes, ou de préférence, en mettant à jour vos types de manière à ce qu’ils soient compatibles. Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

L’exemple suivant génère l’C2259 :

```cpp
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

L’exemple suivant génère l’C2259 :

```cpp
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
