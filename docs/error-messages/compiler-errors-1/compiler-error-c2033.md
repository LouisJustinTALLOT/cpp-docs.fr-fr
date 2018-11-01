---
title: Erreur du compilateur C2033
ms.date: 11/04/2016
f1_keywords:
- C2033
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
ms.openlocfilehash: 8147c707c70e6c3f21ed81b2acf0a59b72065408
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480429"
---
# <a name="compiler-error-c2033"></a>Erreur du compilateur C2033

'identifier' : un champ de bits ne peut pas avoir d’indirection

Le champ de bits a été déclaré en tant que pointeur, ce qui n’est pas autorisé.

L’exemple suivant génère l’erreur C2033 :

```
// C2033.cpp
struct S {
   int *b : 1;  // C2033
};
```

Solution possible :

```
// C2033b.cpp
// compile with: /c
struct S {
   int b : 1;
};
```