---
description: 'En savoir plus sur : Comment : spécifier un paramètre de sortie'
title: 'Procédure : Spécifier un paramètre de sortie'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: b43930557b4bdfd22bf902a6d9adf95eb8ba4d01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286336"
---
# <a name="how-to-specify-an-out-parameter"></a>Procédure : Spécifier un paramètre de sortie

Cet exemple montre comment spécifier qu’un paramètre de fonction est un `out` paramètre, et comment appeler cette fonction à partir d’un programme C#.

Un `out` paramètre est spécifié en C++ à l’aide de <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>Exemple

La première partie de cet exemple crée une DLL C++. Il définit un type qui contient une fonction avec un `out` paramètre.

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

Ce fichier source est un client C# qui utilise le composant C++ créé dans l’exemple précédent.

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
