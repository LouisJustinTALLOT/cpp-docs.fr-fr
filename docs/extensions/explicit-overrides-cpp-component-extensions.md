---
title: Substitutions explicites (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: 7d36793e4467f9454aca1eb207f3c3dfbd483bff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516674"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Substitutions explicites (C++/CLI et C++/CX)

Cette rubrique explique comment remplacer explicitement un membre d’une classe de base ou d’une interface. Une substitution nommée (explicite) ne doit être utilisée que pour remplacer une méthode par une méthode dérivée ayant un nom différent.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Paramètres

*overriding-function-declarator*<br/>
Type de retour, nom et liste d’arguments de la fonction de substitution.  Notez que la fonction de substitution n’a pas à avoir le même nom que la fonction qui est remplacée.

*type*<br/>
Type de base qui contient une fonction à remplacer.

*function*<br/>
Liste d’un ou plusieurs noms de fonctions à remplacer séparés par des virgules.

*overriding-function-definition*<br/>
Instructions de corps de fonction qui définissent la fonction de substitution.

### <a name="remarks"></a>Remarques

Utilisez des substitutions explicites pour créer un alias pour une signature de méthode, ou pour fournir différentes implémentations pour des méthodes avec la même signature.

Pour des informations concernant la modification des types hérités ou de comportement et des membres de type hérités, consultez [Spécificateurs de substitution](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Remarques

Pour plus d’informations sur les substitutions explicites dans du code natif ou compilé avec `/clr:oldSyntax`, consultez [Substitutions explicites](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre une substitution simple, implicite et l’implémentation d’un membre dans une interface de base, sans utiliser de substitutions explicites.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

L’exemple de code suivant montre comment implémenter tous les membres d’interface avec une signature commune, à l’aide de la syntaxe de substitution explicite.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

L’exemple de code suivant montre comment une substitution de fonction peut avoir un nom différent de la fonction qu’elle implémente.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

L’exemple de code suivant montre une implémentation d’interface explicite qui implémente une collection type safe.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)