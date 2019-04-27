---
title: Erreur du compilateur C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230527"
---
# <a name="compiler-error-c2466"></a>Erreur du compilateur C2466

Impossible d’allouer un tableau de taille constante 0

Un tableau est alloué ou déclaré avec une taille égale à zéro. L’expression de constante pour la taille du tableau doit être un entier supérieur à zéro. Une déclaration de tableau avec un indice zéro est autorisée uniquement pour une classe, structure ou membre d’union et uniquement avec les extensions Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

L’exemple suivant génère l’erreur C2466 :

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```