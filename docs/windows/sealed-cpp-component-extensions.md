---
title: sealed (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: bbeaaa6b7d921cca600a665a961307ddac967367
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551227"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++ / c++ / CLI et c++ / CX)

**sealed** est un mot clé contextuel pour les classes ref qui indique qu’un membre virtuel ne peut pas être substitué, ou qu’un type ne peut pas être utilisé comme type de base.

> [!NOTE]
> La norme ISO C ++ 11 Standard langue a introduit le [finale](../cpp/final-specifier.md) mot clé. Utilisez **finale** sur les classes standard et **sealed** sur les classes ref.

## <a name="all-runtimes"></a>Tous les runtimes

## <a name="syntax"></a>Syntaxe

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Paramètres

*identifier*<br/>
Nom de la fonction ou de la classe.

*type de retour*<br/>
Type retourné par une fonction.

## <a name="remarks"></a>Notes

Dans le premier exemple de syntaxe, une classe est sealed. Dans le deuxième exemple, une fonction virtuelle est sealed.

Utilisez le **sealed** mot clé pour les classes ref et leurs fonctions membres virtuelles. Pour plus d’informations, consultez [des spécificateurs de substitution et Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Vous pouvez détecter au moment de la compilation si un type est sealed à l’aide de la `__is_sealed(type)` trait de type. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

**sealed** est un mot clé contextuel.  Pour plus d’informations, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

Consultez [classes et structs Ref](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Aucune note de cette fonctionnalité de langage ne s'applique qu'au Common Language Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

Cet exemple de code suivant montre l’effet de **sealed** sur un membre virtuel.

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

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)