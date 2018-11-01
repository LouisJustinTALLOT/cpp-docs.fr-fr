---
title: Erreur du compilateur C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: 14052fa3676396fe2ffc6ca86196025e7adab7d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650773"
---
# <a name="compiler-error-c2661"></a>Erreur du compilateur C2661

'fonction' : aucune fonction surchargée ne nécessite des paramètres numériques

Causes possibles :

1. Incorrect de paramètres réels dans l’appel de fonction.

1. Déclaration de fonction manquant.

L’exemple suivant génère l’erreur C2661 :

```
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```