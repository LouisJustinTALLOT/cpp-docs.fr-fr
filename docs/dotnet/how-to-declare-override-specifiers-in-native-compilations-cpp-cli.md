---
title: 'Comment : déclarer des spécificateurs de substitution (C++ / c++ / CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1089f2d9326cf268bd76ad59242e2664060b78fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386520"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Comment : déclarer des spécificateurs de substitution dans les compilations natives (C++/CLI)

[sealed](../windows/sealed-cpp-component-extensions.md), [abstraite](../windows/abstract-cpp-component-extensions.md), et [remplacer](../windows/override-cpp-component-extensions.md) sont disponibles dans les compilations qui n’utilisent pas **/ZW** ou [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
>  La norme ISO C ++ 11 Standard langue a la [remplacer](../cpp/override-specifier.md) identificateur et le [finale](../cpp/final-specifier.md) identificateur et les deux sont pris en charge dans Visual Studio, cliquez `final` au lieu de `sealed` dans le code est destiné à être compilé en tant que natif uniquement.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre que `sealed` est valide dans les compilations natives.

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

L’exemple suivant montre que `override` est valide dans les compilations natives.

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

Cet exemple montre que `abstract` est valide dans les compilations natives.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Voir aussi

[Spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md)