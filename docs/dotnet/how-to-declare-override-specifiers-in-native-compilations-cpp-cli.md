---
title: 'Comment : déclarer des spécificateurs de substitution (C + c++ / CLI) | Documents Microsoft'
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
ms.openlocfilehash: 8119ab62ee37320074df401c3986b56f3ea6cbfa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130397"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Comment : déclarer des spécificateurs de substitution dans les compilations natives (C++/CLI)
[sealed](../windows/sealed-cpp-component-extensions.md), [abstraite](../windows/abstract-cpp-component-extensions.md), et [remplacer](../windows/override-cpp-component-extensions.md) sont disponibles dans les compilations qui n’utilisent pas **/ZW** ou [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  La norme ISO C ++ 11 Standard langue a la [remplacer](../cpp/override-specifier.md) identificateur et le [final](../cpp/final-specifier.md) identificateur et les deux sont pris en charge dans Visual Studio utilisez `final` au lieu de `sealed` dans le code qui est destiné à être compilé en mode natif uniquement.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre que `sealed` n’est valide dans les compilations natives.  
  
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
 L’exemple suivant montre que `override` n’est valide dans les compilations natives.  
  
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
 Cet exemple montre que `abstract` n’est valide dans les compilations natives.  
  
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