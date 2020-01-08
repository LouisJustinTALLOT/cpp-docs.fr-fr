---
title: Erreur du compilateur C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: cbe4f95037aabf3b4febc1a8fff5a324773a33b4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301832"
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
