---
title: Erreur du compilateur C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: e4d0e8a1c707374e0e93a5687351a9360fa17c0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756043"
---
# <a name="compiler-error-c2661"></a>Erreur du compilateur C2661

'fonction' : aucune fonction surchargée ne prend de nombre de paramètres

Causes possibles :

1. Paramètres réels incorrects dans l’appel de fonction.

1. Déclaration de fonction manquante.

L’exemple suivant génère l’C2661 :

```cpp
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```
