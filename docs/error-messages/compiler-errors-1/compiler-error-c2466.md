---
description: 'En savoir plus sur : erreur du compilateur C2466'
title: Erreur du compilateur C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 68ff57de2c0287f24ac84466ac8053bf73f88a95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333836"
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
