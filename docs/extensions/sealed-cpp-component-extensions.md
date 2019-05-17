---
title: sealed (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: 493f6597d146480714848b37154cc8bacd37113a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516004"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++/CLI et C++/CX)

**sealed** est un mot clé contextuel pour les classes de référence qui indique qu’un membre virtuel ne peut pas être remplacé ou qu’un type ne peut pas être utilisé comme type de base.

> [!NOTE]
> Le langage standard ISO C++11 introduit le mot clé [final](../cpp/final-specifier.md). Utilisez **final** sur les classes standard et **sealed** sur les classes de référence.

## <a name="all-runtimes"></a>Tous les runtimes

## <a name="syntax"></a>Syntaxe

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Paramètres

*identifier*<br/>
Nom de la fonction ou de la classe.

*return-type*<br/>
Type retourné par une fonction.

## <a name="remarks"></a>Remarques

Dans le premier exemple de syntaxe, une classe est sealed. Dans le deuxième exemple, une fonction virtuelle est sealed.

Utilisez le mot clé **sealed** pour les classes de référence et leurs fonctions membres virtuelles. Pour plus d’informations, consultez [Spécificateurs de substitution et compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Vous pouvez détecter au moment de la compilation si un type est sealed à l’aide de la caractéristique de type `__is_sealed(type)`. Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](compiler-support-for-type-traits-cpp-component-extensions.md).

**sealed** est un mot clé contextuel.  Pour plus d’informations, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

Consultez [Classes et structures de référence](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Common Language Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple de code suivant montre l’effet de **sealed** sur un membre virtuel.

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

L'exemple de code suivant montre comment marquer une classe comme sealed.

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)