---
title: Erreur du compilateur C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745978"
---
# <a name="compiler-error-c3149"></a>Erreur du compilateur C3149

'type' : impossible d’utiliser ce type ici sans un’Char’de niveau supérieur

Une déclaration n’a pas été spécifiée correctement.

Par exemple, vous avez peut-être défini un type CLR au niveau de la portée globale et essayé de créer une variable du type dans le cadre de la définition. Étant donné que les variables globales des types CLR ne sont pas autorisées, le compilateur génère C3149.

Pour résoudre cette erreur, déclarez des variables de types CLR à l’intérieur d’une définition de fonction ou de type.

L’exemple suivant génère l’C3149 :

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

L’exemple suivant génère l’C3149 :

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
