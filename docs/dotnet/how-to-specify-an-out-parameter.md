---
title: 'Comment : spécifier un paramètre de sortie'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 4bd6ad1d3009adcc124bdeb90d9d67de07112de2
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912794"
---
# <a name="how-to-specify-an-out-parameter"></a>Comment : spécifier un paramètre de sortie

Cet exemple montre comment spécifier qu’un paramètre de fonction est un paramètre `out` et comment appeler cette fonction à partir d’un C# programme.

Un paramètre `out` est spécifié dans C++ à l’aide de <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Exemple

La première partie de cet exemple crée une C++ dll. Il définit un type qui contient une fonction avec un paramètre `out`.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

Ce fichier source est un C# client qui utilise le C++ composant créé dans l’exemple précédent.

```csharp
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
