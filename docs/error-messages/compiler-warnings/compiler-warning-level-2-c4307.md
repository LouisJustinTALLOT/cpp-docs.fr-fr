---
title: Avertissement du compilateur (niveau 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052064"
---
# <a name="compiler-warning-level-2-c4307"></a>Avertissement du compilateur (niveau 2) C4307

'opérateur' : dépassement de constante intégrale

L’opérateur est utilisé dans une expression qui entraîne un dépassement de la constante entière de l’espace qui lui est alloué. Vous devrez peut-être utiliser un plus grand type pour la constante. Un **entier signé** contient une valeur inférieure à celle d’un `unsigned int`, car l' **entier signé** utilise un bit pour représenter le signe.

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