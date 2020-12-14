---
description: 'En savoir plus sur : erreur du compilateur C3391'
title: Erreur du compilateur C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 1bac535136b2c6115bf0f5ff31c9e098407e03bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313396"
---
# <a name="compiler-error-c3391"></a>Erreur du compilateur C3391

'type_arg' : argument de type non valide pour le paramètre générique’param’du générique’generic_type', doit être un type valeur n’acceptant pas les valeurs null

Un type générique a été instancié de manière incorrecte. Vérifiez la définition du type. Pour plus d’informations, consultez <xref:System.Nullable> et [génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise C# pour créer un composant qui contient un type générique dont certaines contraintes ne sont pas prises en charge lors de la création de types génériques en C++/CLI. Pour plus d’informations, consultez [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Lorsque le composant C3391.dll est disponible, l’exemple suivant génère C3391.

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```
