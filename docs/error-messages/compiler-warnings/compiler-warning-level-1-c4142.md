---
title: Avertissement du compilateur (niveau 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 3c9ab9c22d41e7732c86d43f5c6b4f09c50bbda8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196849"
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
