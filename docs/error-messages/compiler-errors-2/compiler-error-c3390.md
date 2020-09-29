---
title: Erreur du compilateur C3390
description: Erreur du compilateur Microsoft C++ C3390, ses causes et comment les résoudre.
ms.date: 09/26/2020
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 467b379d7f5a349a217b566dc55b28d5fbd789da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414358"
---
# <a name="compiler-error-c3390"></a>Erreur du compilateur C3390

> '*type_arg*' : argument de type non valide pour le paramètre générique'*param*'du générique'*generic_type*', doit être un type référence

Un type générique a été instancié de manière incorrecte. Vérifiez la définition du type.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

Le premier exemple utilise C# pour créer un composant qui contient un type générique. Ce type a certaines contraintes qui ne sont pas prises en charge lors de la création de types génériques en C++/CLI. Pour plus d’informations, consultez [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Lorsque le composant C3390.dll est disponible, l’exemple suivant génère C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK - do this instead
}
```
