---
description: 'En savoir plus sur : nouveau (nouvel emplacement dans vtable) (C++/CLI et C++/CX)'
title: nouveau (nouvel emplacement dans vtable) (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: ccc6adbd29eca82b44d34b981803a88332a8784a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257675"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>nouveau (nouvel emplacement dans vtable) (C++/CLI et C++/CX)

Le **`new`** mot clé indique qu’un membre virtuel obtiendra un nouvel emplacement dans la vtable.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

Non pris en charge dans Windows Runtime.

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Dans une `/clr` compilation, **`new`** indique qu’un membre virtuel obtiendra un nouvel emplacement dans la vtable ; que la fonction ne substitue pas à une méthode de classe de base.

**`new`** fait en sorte que le modificateur newslot soit ajouté au langage intermédiaire pour la fonction.  Pour plus d’informations sur newslot, consultez :

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant montre l’effet de **`new`** .

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

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Spécificateurs de substitution](override-specifiers-cpp-component-extensions.md)
