---
title: Erreur du compilateur C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 4c0544df55fc71ace697d7e0a53ba303706e1378
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201121"
---
# <a name="compiler-error-c3390"></a>Erreur du compilateur C3390

'type_arg' : argument de type non valide pour le paramètre générique 'param' du générique 'generic_type', doit être un type référence

Un type générique a été instancié de manière incorrecte.  Vérifiez la définition du type.  Pour plus d’informations, consultez la page [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

Le premier exemple utilise C# pour créer un composant qui contient un type générique qui a certaines contraintes qui ne sont pas prises en charge lors de la C++création de types génériques dans/CLR. Pour plus d’informations, consultez [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Lorsque le composant C3390. dll est disponible, l’exemple suivant génère C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```
