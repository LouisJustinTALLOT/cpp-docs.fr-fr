---
title: Compilateur avertissement (niveau 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302278"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilateur avertissement (niveau 1) C4142

redéfinition bénigne du type

Un type est redéfini d’une manière qui n’a aucun effet sur le code généré.

Les causes possibles sont les suivantes :

- Une fonction membre d’une classe dérivée a un type de retour différent à partir de la fonction membre correspondante de la classe de base.

- Un type défini avec la `typedef` commande est redéfinie avec une syntaxe différente.

L’exemple suivant génère l’erreur C4142 :

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```