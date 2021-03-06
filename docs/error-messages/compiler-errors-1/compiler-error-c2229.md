---
description: 'En savoir plus sur : erreur du compilateur C2229'
title: Erreur du compilateur C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: d95d1248ec7e555af0c4ecfffa25dc69af288458
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194980"
---
# <a name="compiler-error-c2229"></a>Erreur du compilateur C2229

le type’identifier’a un tableau de taille zéro non conforme

Un membre d’une structure ou d’un champ de bits contient un tableau de taille zéro qui n’est pas le dernier membre.

Étant donné que vous pouvez avoir un tableau de taille zéro comme dernier membre de la structure, vous devez spécifier sa taille lorsque vous allouez la structure.

Si le tableau de taille zéro n’est pas le dernier membre de la structure, le compilateur ne peut pas calculer le décalage pour les champs restants.

L’exemple suivant génère l’C2229 :

```cpp
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```
