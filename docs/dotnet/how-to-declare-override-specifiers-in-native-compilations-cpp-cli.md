---
title: 'Comment : Déclarer les spéculateurs de remplacement (C/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374453"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Comment : déclarer des spécificateurs de substitution dans les compilations natives (C++/CLI)

[scellés,](../extensions/sealed-cpp-component-extensions.md) [abstraits,](../extensions/abstract-cpp-component-extensions.md)et [de remplacement](../extensions/override-cpp-component-extensions.md) sont disponibles dans les compilations qui n’utilisent pas **/ZW** ou [/clr](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> La langue standard ISO C-11 a l’identifiant [de remplacement](../cpp/override-specifier.md) et l’identifiant `sealed` [final,](../cpp/final-specifier.md) et les deux sont pris en charge dans Visual Studio Use `final` au lieu de dans le code qui est censé être compilé comme natif seulement.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant `sealed` montre que c’est valable dans les compilations natives.

### <a name="code"></a>Code

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant `override` montre que c’est valable dans les compilations natives.

### <a name="code"></a>Code

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Cet exemple `abstract` montre que cela est valable dans les compilations natives.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Voir aussi

[Spécificateurs de substitution](../extensions/override-specifiers-cpp-component-extensions.md)
