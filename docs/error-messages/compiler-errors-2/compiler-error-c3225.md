---
title: Erreur du compilateur C3225 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d8b1251b9c13a71faf771c85924a75681deab7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033249"
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