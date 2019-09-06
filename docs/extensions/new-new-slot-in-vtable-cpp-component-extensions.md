---
title: nouveau (nouvel emplacement dans vtable) (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: 684c6149457f7b0306f3d444a3652ecda1636839
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "70311804"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>nouveau (nouvel emplacement dans vtable) (C++/CLI et C++/CX)

Le mot clé **new** indique qu’un membre virtuel obtient un nouvel emplacement dans la vtable.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

Non pris en charge dans Windows Runtime.

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Dans une compilation `/clr`, **new** indique qu’un membre virtuel va obtenir un nouvel emplacement dans la vtable ; que la fonction ne remplace pas une méthode de classe de base.

**new** entraîne l’ajout du modificateur newslot au langage intermédiaire de la fonction.  Pour plus d’informations sur newslot, consultez :

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant illustre l’effet de **new**.

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

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Spécificateurs de substitution](override-specifiers-cpp-component-extensions.md)
