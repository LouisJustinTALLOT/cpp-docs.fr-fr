---
description: 'En savoir plus sur : erreur du compilateur C2228'
title: Erreur du compilateur C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 8bf5c4af88f77237699baae5e7a458fca971f126
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195058"
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
