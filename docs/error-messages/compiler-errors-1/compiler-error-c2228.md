---
title: Erreur du compilateur C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 20e295d09e39a12ed8163ec980fa304cd4167218
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404336"
---
# <a name="compiler-error-c2228"></a>Erreur du compilateur C2228

la partie gauche de '.identifier' doit avoir un class/struct/union

L’opérande à gauche de l’opérateur point (.) n’est pas une classe, une structure ou une union.

L’exemple suivant génère l’erreur C2228 :

```
// C2228.cpp
int i;
struct S {
public:
    int member;
} s, *ps = &s;

int main() {
   i.member = 0;   // C2228 i is not a class type
   ps.member = 0;  // C2228 ps is a pointer to a structure

   s.member = 0;   // s is a structure type
   ps->member = 0; // ps points to a structure S
}
```

Vous recevez également cette erreur si vous utilisez une syntaxe incorrecte lors de l’utilisation des Extensions managées. Si vous pouvez utiliser l’opérateur point pour accéder au membre d’une classe managée dans d’autres langages de Visual Studio, un pointeur vers l’objet en C++ signifie que vous devez utiliser l’opérateur -> pour accéder au membre :

Incorrect : `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

Correct : `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`