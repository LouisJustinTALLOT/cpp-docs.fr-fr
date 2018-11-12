---
title: Avertissement du compilateur (niveau 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: e9ad30f60260893130beed921aab811c894868cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528152"
---
# <a name="compiler-warning-level-2-c4307"></a>Avertissement du compilateur (niveau 2) C4307

'opérateur' : dépassement de constante intégrale

L’opérateur est utilisé dans une expression qui aboutit à une constante entière un débordement de l’espace alloué pour celui-ci. Vous devrez peut-être utiliser un type plus grand pour la constante. Un **type signed int** contient une valeur inférieure à celle un `unsigned int` , car le **type signed int** utilise un bit pour représenter le signe.

L’exemple suivant génère l’erreur C4307 :

```
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```