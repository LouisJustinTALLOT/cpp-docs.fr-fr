---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4383'
title: Avertissement du compilateur (niveau 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: f6ece51ed497919cf444952f42130cc3a4bfb4a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339928"
---
# <a name="compiler-warning-level-1-c4383"></a>Avertissement du compilateur (niveau 1) C4383

'instance_dereference_operator' : la signification du déréférencement d’un handle peut changer, lorsqu’un opérateur’operator’défini par l’utilisateur existe ; écrire l’opérateur en tant que fonction statique pour être explicite à propos de l’opérande

Quand vous ajoutez une substitution d’instance définie par l’utilisateur de l’opérateur de déréférencement dans un type managé, vous substituez potentiellement la capacité de l’opérateur de déréférence du type à retourner l’objet du handle. Envisagez d’écrire un opérateur de déréférencement statique défini par l’utilisateur.

Pour plus d’informations, consultez [handle to Object Operator (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) and [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

En outre, un opérateur d’instance n’est pas disponible pour d’autres compilateurs de langage par le biais de métadonnées référencées. Pour plus d’informations, consultez [opérateurs définis par l’utilisateur (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4383.

```cpp
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```
