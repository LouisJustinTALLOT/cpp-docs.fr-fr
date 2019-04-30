---
title: 'Procédure : Spécifiez un hors paramètre'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 901257b92aaa5e13e6e79d612ca590b734e15881
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387214"
---
# <a name="how-to-specify-an-out-parameter"></a>Procédure : Spécifiez un hors paramètre

Cet exemple montre comment spécifier qu’un paramètre de fonction est un paramètre de sortie et comment appeler cette fonction à partir d’un programme c#.

Un paramètre de sortie est spécifié dans Visual C++ avec <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>Exemple

La première partie de cet exemple est une DLL Visual C++ avec un type qui contient une fonction avec un paramètre de sortie.

```
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

Il s’agit d’un client c# qui consomme le composant Visual C++ créé dans l’exemple précédent.

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
