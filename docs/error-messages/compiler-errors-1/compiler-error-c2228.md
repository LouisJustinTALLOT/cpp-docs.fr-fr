---
title: Erreur du compilateur C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 56eed6aeff5a955253a440d5931d66118f4604e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759280"
---
# <a name="compiler-error-c2228"></a>Erreur du compilateur C2228

la partie gauche de '.identifier' doit avoir un class/struct/union

L’opérande à gauche du point (.) n’est pas une classe, une structure ou une Union.

L’exemple suivant génère l’erreur C2228 :

```cpp
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
