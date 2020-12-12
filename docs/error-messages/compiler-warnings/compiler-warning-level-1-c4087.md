---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4087'
title: Avertissement du compilateur (niveau 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: 2375ad5c99862f7ee8a0156ca1b3d637b95f0569
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267545"
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
