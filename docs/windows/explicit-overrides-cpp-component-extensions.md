---
title: Substitutions explicites (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ce2f65fd740fd2bf133d65b25cbb52838c53dd2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601210"
---
# <a name="explicit-overrides--c-component-extensions"></a>Substitutions explicites  (extensions du composant C++)

Cette rubrique explique comment substituer explicitement un membre d’une classe de base ou une interface. Une substitution nommée (explicite) doit uniquement être utilisée pour substituer une méthode par une méthode dérivée qui a un nom différent.

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Paramètres

*substitution de déclarateur de fonction*  
La liste de type, le nom et argument de retour de la fonction de substitution.  Notez que la fonction de substitution n’a pas d’avoir le même nom que la fonction qui est substitué.

*type*  
Le type de base qui contient une fonction à remplacer.

*function*  
Une liste délimitée par des virgules d’un ou plusieurs noms de fonction à remplacer.

*substitution de définition de fonction*  
Les instructions de corps de fonction qui définissent la fonction de substitution.

### <a name="remarks"></a>Notes

Utilisez explicite les remplacements pour créer un alias pour une signature de méthode, ou pour fournir des implémentations différentes pour les méthodes en utilisant la même signature.

Pour savoir comment modifier le comportement des types hérités et les membres de type hérité, consultez [des spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Notes

Pour plus d’informations sur explicite remplace en code natif ou code compilé avec `/clr:oldSyntax`, consultez [substitutions explicites](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre un remplacement simple, implicite et l’implémentation d’un membre dans une interface de base, ne pas à l’aide de substitutions explicites.

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

L’exemple de code suivant montre comment une substitution de la fonction peut avoir un nom différent à partir de la fonction qu’il implémente.

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

L’exemple de code suivant montre une implémentation d’interface explicite qui implémente une collection de types-safe.

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

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)