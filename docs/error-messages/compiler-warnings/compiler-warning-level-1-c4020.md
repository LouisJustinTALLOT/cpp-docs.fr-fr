---
title: Avertissement du compilateur (niveau 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: ccab8eaac42932491fc8b88cd28f2d3334b2e849
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626322"
---
# <a name="compiler-warning-level-1-c4020"></a>Avertissement du compilateur (niveau 1) C4020

'fonction' : paramètres réels trop nombreux

Le nombre de paramètres réels dans un appel de fonction dépasse le nombre de paramètres formels dans le prototype ou la définition de la fonction. Le compilateur passe les paramètres réels supplémentaires en fonction de la Convention d’appel de la fonction.

L’exemple suivant génère l’C4020 :

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Solution possible :

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```