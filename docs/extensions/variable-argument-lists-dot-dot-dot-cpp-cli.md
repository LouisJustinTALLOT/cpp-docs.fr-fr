---
title: Listes d'arguments de variable (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 4db75653251a558d6f43f5be63098fbb26e1e6ff
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912848"
---
# <a name="variable-argument-lists--ccli"></a>Listes d'arguments de variable (...) (C++/CLI)

Cet exemple montre comment utiliser la syntaxe `...` dans C++/CLI pour implémenter des fonctions qui ont un nombre variable d’arguments.

> [!NOTE]
> Cette rubrique concerne C++/CLI. Pour plus d’informations sur l’utilisation de `...` dans la version ISO C++ standard, consultez [Ellipses et modèles variadiques](../cpp/ellipses-and-variadic-templates.md) et Ellipses et arguments par défaut dans [Expressions suffixées](../cpp/postfix-expressions.md).

Le paramètre qui utilise `...` doit être le dernier paramètre dans la liste de paramètres.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Exemple de code

L’exemple suivant montre comment appeler une fonction Visual C++ qui accepte un nombre variable d’arguments à partir de C#.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

La fonction `f` peut être appelée à partir de C# ou de Visual Basic, par exemple, comme s’il s’agissait d’une fonction qui accepte un nombre variable d’arguments.

Dans C#, un argument passé à un paramètre `ParamArray` peut être appelé par un nombre variable d’arguments. L’exemple de code suivant est en C#.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Un appel à `f` dans Visual C++ peut passer un tableau initialisé ou un tableau de longueur variable.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>Voir aussi

[Tableaux](arrays-cpp-component-extensions.md)