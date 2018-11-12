---
title: New (nouvel emplacement dans vtable) (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: b143b2ead1165382d0959f4e4c90f1d2e7ea936a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487163"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>New (nouvel emplacement dans vtable) (C++ / c++ / CLI et c++ / CX)

Le **nouveau** mot-clé indique qu’un membre virtuel obtiendra un nouvel emplacement dans vtable.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

Pas de prise en charge dans Windows Runtime.

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Dans un `/clr` compilation, **nouveau** indique qu’un membre virtuel obtiendra un nouvel emplacement dans vtable ; que la fonction ne remplace pas une méthode de classe de base.

**nouvelle** provoque le modificateur newslot à ajouter à l’IL de la fonction.  Pour plus d’informations sur newslot, consultez :

- [MethodInfo.GetBaseDefinition (méthode)](https://msdn.microsoft.com/library/system.reflection.methodinfo.getbasedefinition.aspx)

- [Énumération MethodAttributes](https://msdn.microsoft.com/library/system.reflection.methodattributes.aspx)

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant montre l’effet de **nouveau**.

```cpp
// newslot.cpp
// compile with: /clr
ref class C {
public:
   virtual void f() {
      System::Console::WriteLine("C::f() called");
   }

   virtual void g() {
      System::Console::WriteLine("C::g() called");
   }
};

ref class D : public C {
public:
   virtual void f() new {
      System::Console::WriteLine("D::f() called");
   }

   virtual void g() override {
      System::Console::WriteLine("D::g() called");
   }
};

ref class E : public D {
public:
   virtual void f() override {
      System::Console::WriteLine("E::f() called");
   }
};

int main() {
   D^ d = gcnew D;
   C^ c = gcnew D;

   c->f();   // calls C::f
   d->f();   // calls D::f

   c->g();   // calls D::g
   d->g();   // calls D::g

   D ^ e = gcnew E;
   e->f();   // calls E::f
}
```

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)<br/>

[Spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md)