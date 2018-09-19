---
title: Compilateur avertissement (niveau 2) C4307 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed18c213b35e79aaae98efa5932ac404a8d84bff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079191"
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