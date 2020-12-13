---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4307'
title: Avertissement du compilateur (niveau 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: 5de4279d430f3275d61c6dca3d9db161c4ac5f11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339206"
---
# <a name="compiler-warning-level-2-c4307"></a>Avertissement du compilateur (niveau 2) C4307

'opérateur' : dépassement de constante intégrale

L’opérateur est utilisé dans une expression qui entraîne un dépassement de la constante entière de l’espace qui lui est alloué. Vous devrez peut-être utiliser un plus grand type pour la constante. Un **`signed int`** contient une valeur inférieure à un **`unsigned int`** , car **`signed int`** utilise un bit pour représenter le signe.

L’exemple suivant génère l’C4307 :

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```
