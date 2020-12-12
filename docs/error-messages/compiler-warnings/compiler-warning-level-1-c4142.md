---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4142'
title: Avertissement du compilateur (niveau 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: d82403d79310d577cd45fe835cd486719ea0fdc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115727"
---
# <a name="compiler-warning-level-1-c4142"></a>Avertissement du compilateur (niveau 1) C4142

redéfinition bénigne du type

Un type est redéfini de manière à ne pas avoir d’effet sur le code généré.

Les causes possibles sont les suivantes :

- Une fonction membre d’une classe dérivée a un type de retour différent de la fonction membre correspondante de la classe de base.

- Un type défini avec la **`typedef`** commande est redéfini à l’aide d’une syntaxe différente.

L’exemple suivant génère l’C4142 :

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
