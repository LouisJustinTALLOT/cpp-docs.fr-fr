---
title: Erreur du compilateur C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: ed645535300e0a7c4d27f8bed43d3143bae7e97a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742864"
---
# <a name="compiler-error-c3225"></a>Erreur du compilateur C3225

l’argument de type générique pour’arg’ne peut pas être’type', il doit s’agir d’un type valeur ou d’un type de handle

L’argument de type générique n’est pas du type correct.

Pour plus d’informations, consultez [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="examples"></a>Exemples

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

L’exemple suivant crée un composant à l’aide de C#. Notez que la contrainte spécifie que le type générique peut uniquement être instancié avec un type valeur.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

Cet exemple utilise le composant créé par C# et viole la contrainte selon laquelle MyList ne peut être instancié qu’avec un type valeur autre que <xref:System.Nullable> . L’exemple suivant génère l’C3225.

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
