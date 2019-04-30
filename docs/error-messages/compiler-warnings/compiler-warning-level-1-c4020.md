---
title: Compilateur avertissement (niveau 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 75148c210ddd2a611061d58c036d12c084f442cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400044"
---
# <a name="compiler-warning-level-1-c4020"></a>Compilateur avertissement (niveau 1) C4020

'fonction' : paramètres réels trop nombreux

Le nombre de paramètres réels dans un appel de fonction dépasse le nombre de paramètres formels dans la définition ou le prototype de fonction. Le compilateur passe les paramètres réels supplémentaires en fonction de la convention d’appel de la fonction.

L’exemple suivant génère l’erreur C4020 :

```
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Solution possible :

```
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```