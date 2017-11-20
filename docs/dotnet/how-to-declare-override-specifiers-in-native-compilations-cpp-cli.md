---
title: "Comment : déclarer des spécificateurs de substitution (C + c++ / CLI) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07d612e97a6aaf3ff53116415b8eedc7324f78ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
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