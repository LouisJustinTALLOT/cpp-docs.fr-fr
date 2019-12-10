---
title: 'Comment : spécifier un paramètre Out'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 5f0b462e672de4408d50bf95d65c749bf1881078
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988436"
---
# <a name="how-to-specify-an-out-parameter"></a>Comment : spécifier un paramètre Out

Cet exemple montre comment spécifier qu’un paramètre de fonction est un paramètre de sortie et comment appeler cette fonction à partir C# d’un programme.

Un paramètre de sortie est spécifié dans C++ Visual avec <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Exemple

La première partie de cet exemple est une dll C++ Visual avec un type qui contient une fonction avec un paramètre out.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>Exemple

Il s’agit C# d’un client qui utilise le C++ composant visuel créé dans l’exemple précédent.

```
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
