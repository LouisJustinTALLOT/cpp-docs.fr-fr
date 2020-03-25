---
title: literal (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: 8c40adaed32bae23ec43cd553c3f755ac2b54cfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172137"
---
# <a name="literal-ccli-and-ccx"></a>literal (C++/CLI et C++/CX)

Une variable (membre de données) marquée comme **literal** dans une compilation **/CLR** est l’équivalent natif d’une variable **static const**.

## <a name="all-platforms"></a>Toutes les plateformes

### <a name="remarks"></a>Notes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

### <a name="remarks"></a>Notes

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Notes

Un membre de données marqué comme **literal** doit être initialisé lorsqu’il est déclaré, et la valeur doit être un type constant, integral, enum ou string. La conversion du type de l’expression d’initialisation en type de membre de données static const ne doit pas nécessiter une conversion définie par l’utilisateur.

Aucune mémoire n’est allouée pour le champ literal au moment du runtime ; le compilateur insère uniquement sa valeur dans les métadonnées pour la classe.

Une variable marquée **static const** ne sera pas disponible dans les métadonnées pour les autres compilateurs.

Pour plus d’informations, consultez [Static](../cpp/storage-classes-cpp.md) et [const](../cpp/const-cpp.md).

**literal** est un mot clé contextuel. Pour plus d’informations, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="example"></a>Exemple

Cet exemple montre qu’une variable **literal** implique une variable **static**.

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

## <a name="example"></a>Exemple

L’exemple suivant montre l’effet de la variable literal sur les métadonnées :

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Notez la différence entre `sc` et `lit` dans les métadonnées : la directive `modopt` est appliquée à `sc`, ce qui signifie qu’elle peut être ignorée par d’autres compilateurs.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Exemple

L’exemple suivant, créé dans C#, référence les métadonnées créées dans l’exemple précédent et présente l’effet des variables **literal** et **static const** :

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

## <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
