---
description: 'En savoir plus sur : erreur du compilateur C2661'
title: Erreur du compilateur C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: 524d270fd15b529bad13a5ff1e5e46f3d5d9dd04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170020"
---
# <a name="compiler-error-c2661"></a>Erreur du compilateur C2661

'fonction' : aucune fonction surchargée ne prend de nombre de paramètres

Causes possibles :

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
