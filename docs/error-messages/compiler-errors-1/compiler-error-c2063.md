---
title: Erreur du compilateur C2063
ms.date: 11/04/2016
f1_keywords:
- C2063
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
ms.openlocfilehash: 5d91dc595798793899eb8ac33e2a6c71cabad02a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408639"
---
# <a name="compiler-error-c2063"></a>Erreur du compilateur C2063

'identifier' : n’est pas une fonction

L’identificateur est utilisé comme fonction mais il n’est pas déclaré en tant que fonction.

L’exemple suivant génère l’erreur C2063 :

```
// C2063.c
int main() {
   int i, j;
   j = i();    // C2063, i is not a function
}
```

Solution possible :

```
// C2063b.c
int i() { return 0;}
int main() {
   int j;
   j = i();
}
```