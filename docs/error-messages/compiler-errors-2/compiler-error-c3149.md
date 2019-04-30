---
title: Erreur du compilateur C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345514"
---
# <a name="compiler-error-c3149"></a>Erreur du compilateur C3149

'type' : Impossible d’utiliser ce type ici sans un niveau supérieur 'char'

Une déclaration n’a pas été spécifiée correctement.

Par exemple, peut avoir défini un type CLR dans une portée globale et a tenté de créer une variable du type en tant que partie de la définition. Étant donné que les variables globales de types CLR ne sont pas autorisées, le compilateur générera C3149.

Pour résoudre cette erreur, déclarez les variables de types CLR à l’intérieur d’une définition de fonction ou type.

L’exemple suivant génère l’erreur C3149 :

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

L’exemple suivant génère l’erreur C3149 :

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
