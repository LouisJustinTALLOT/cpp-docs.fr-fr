---
title: Erreur du compilateur C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743820"
---
# <a name="compiler-error-c2466"></a>Erreur du compilateur C2466

Impossible d’allouer un tableau de taille constante 0

Un tableau est alloué ou déclaré avec la taille zéro. L’expression constante pour la taille du tableau doit être un entier supérieur à zéro. Une déclaration de tableau avec un indice zéro est légale uniquement pour un membre de classe, de structure ou d’Union et uniquement avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

L’exemple suivant génère l’C2466 :

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
