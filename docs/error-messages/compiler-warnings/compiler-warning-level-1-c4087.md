---
title: Avertissement du compilateur (niveau 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: fe2b4fadfb87726e81178a3530299dbb8620aec9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626840"
---
# <a name="compiler-warning-level-1-c4087"></a>Avertissement du compilateur (niveau 1) C4087

'fonction' : déclaré avec une liste de paramètres 'void'

La déclaration de fonction n’a aucun paramètre formel, mais l’appel de fonction a des paramètres réels. Des paramètres supplémentaires sont passés selon la convention d’appel de la fonction.

Cet avertissement concerne le compilateur C.

## <a name="example"></a>Exemple

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```