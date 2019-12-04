---
title: Erreur du compilateur C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 1caa1e7ce787ffc14e615c946b5d670c75e0332a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757616"
---
# <a name="compiler-error-c3225"></a>Erreur du compilateur C3225

l’argument de type générique pour’arg’ne peut pas être’type', il doit s’agir d’un type valeur ou d’un type de handle

L’argument de type générique n’est pas du type correct.

Pour plus d’informations, consultez la page [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

Vous ne pouvez pas instancier un type générique avec un type natif. L’exemple suivant génère l’C3225.

```cpp
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

L’exemple suivant crée un composant à C#l’aide de. Notez que la contrainte spécifie que le type générique peut uniquement être instancié avec un type valeur.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Exemple

Cet exemple consomme le C#composant créé et viole la contrainte selon laquelle myList peut uniquement être instancié avec un type valeur autre que <xref:System.Nullable>. L’exemple suivant génère l’C3225.

```cpp
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
