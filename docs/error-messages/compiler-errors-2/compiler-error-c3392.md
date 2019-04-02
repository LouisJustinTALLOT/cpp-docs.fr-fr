---
title: Erreur du compilateur C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 72bdef1b3344b3d69ba0d014f92a85e9381de4b3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779532"
---
# <a name="compiler-error-c3392"></a>Erreur du compilateur C3392

'arg_type' : argument de type non valide pour le paramètre générique 'param' du générique 'type-générique', doit posséder un constructeur sans paramètre public

Un type générique a été instancié de manière incorrecte. Vérifiez la définition du type. Pour plus d’informations, consultez [génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise c# pour créer un composant qui contient un type générique qui a certaines contraintes ne sont pas pris en charge lors de la création de types génériques en C / c++ / CLI. Pour plus d’informations, consultez [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Lorsque le composant C3392.dll est disponible, l’exemple suivant génère l’erreur C3392.

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```