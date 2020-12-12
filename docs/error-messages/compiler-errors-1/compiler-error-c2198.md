---
description: 'En savoir plus sur : erreur du compilateur C2198'
title: Erreur du compilateur C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: 60c07bdaa422a3844bf17355fd88e7924ce05dc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170033"
---
# <a name="compiler-error-c2198"></a>Erreur du compilateur C2198

'function' : pas assez d’arguments pour un appel

Le compilateur a détecté un nombre insuffisant de paramètres pour un appel à la fonction, ou une déclaration de fonction incorrecte.

L’exemple suivant génère l’erreur C2198 :

```c
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```
