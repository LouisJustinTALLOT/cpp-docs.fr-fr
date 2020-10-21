---
title: littéral (C++/CLI)
description: Le mot clé Literal est un mot clé contextuel Microsoft C++/CLI pour une constante au moment de la compilation.
ms.date: 10/20/2020
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.openlocfilehash: 2d71a535252ba51f89407670b474a34b407eaffc
ms.sourcegitcommit: 59b7c18703d1ffd66827db0e2eeece490d3d8789
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92337211"
---
# <a name="literal-ccli"></a>`literal` (C++/CLI)

Une variable (membre de données) marquée comme **`literal`** dans une **`/clr`** compilation est une constante au moment de la compilation. Il s’agit de l’équivalent natif d’une [`const`](/dotnet/csharp/language-reference/keywords/const) variable C#.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="remarks"></a>Remarques

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Remarques

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Remarques

Un membre de données marqué comme **`literal`** doit être initialisé lorsqu’il est déclaré. Et, la valeur doit être un type intégral, enum ou chaîne constant. La conversion du type de l’expression d’initialisation en type du membre de **`literal`** données ne peut pas nécessiter une conversion définie par l’utilisateur.

Aucune mémoire n’est allouée pour le **`literal`** champ au moment de l’exécution ; le compilateur insère uniquement sa valeur dans les métadonnées de la classe. La **`literal`** valeur est traitée comme une constante au moment de la compilation. L’équivalent le plus proche dans le C++ standard est **`constexpr`** , mais un membre de données ne peut pas être **`constexpr`** en c++/CLI.

Une variable marquée comme **`literal`** diffère d’une variable marquée **`static const`** . Un **`static const`** membre de données n’est pas mis à disposition dans les métadonnées d’autres compilateurs. Pour plus d’informations, consultez [`static`](../cpp/storage-classes-cpp.md) et [`const`](../cpp/const-cpp.md).

**`literal`** est un mot clé contextuel. Pour plus d’informations, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Exemples

Cet exemple montre qu’une **`literal`** variable implique **`static`** .

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

L’exemple suivant montre l’effet de **`literal`** dans les métadonnées :

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Notez la différence entre `sc` et `lit` dans les métadonnées : la directive `modopt` est appliquée à `sc`, ce qui signifie qu’elle peut être ignorée par d’autres compilateurs.

```MSIL
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x00000001)
```

```MSIL
.field public static literal int32 lit = int32(0x00000000)
```

L’exemple suivant, créé en C#, référence les métadonnées créées dans l’exemple précédent et montre l’effet des **`literal`** **`static const`** variables et :

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
