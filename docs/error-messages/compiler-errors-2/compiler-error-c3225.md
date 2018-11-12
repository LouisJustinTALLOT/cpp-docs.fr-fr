---
title: Erreur du compilateur C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 81316864c9c04c18ca1c96d1e74ad9988734eb72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541490"
---
# <a name="compiler-error-c3225"></a>Erreur du compilateur C3225

argument de type générique de 'arg' ne peut pas être 'type', il doit être un type valeur ou type de handle

L’argument de type générique n’était pas du type correct.

Pour plus d’informations, consultez la page [Génériques](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

Vous ne pouvez pas instancier un type générique avec un type natif. L’exemple suivant génère C3225.

```
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>Exemple

L’exemple suivant crée un composant à l’aide de c#. Notez que la contrainte spécifie que le type générique peut uniquement être instancié avec un type valeur.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Exemple

Cet exemple utilise le langage c#-composant créé et viole la contrainte MyList ne peut être instancié avec un type valeur autre que <xref:System.Nullable>. L’exemple suivant génère C3225.

```
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```