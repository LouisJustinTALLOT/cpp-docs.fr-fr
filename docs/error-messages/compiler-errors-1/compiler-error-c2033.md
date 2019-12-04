---
title: Erreur du compilateur C2033
ms.date: 11/04/2016
f1_keywords:
- C2033
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
ms.openlocfilehash: 6fec222117f28e885d6187e6733559433f4943d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750960"
---
# <a name="compiler-error-c2033"></a>Erreur du compilateur C2033

'identifier' : un champ de bits ne peut pas avoir d’indirection

Le champ de bits a été déclaré en tant que pointeur, ce qui n’est pas autorisé.

L’exemple suivant génère l’erreur C2033 :

```cpp
// C2033.cpp
struct S {
   int *b : 1;  // C2033
};
```

Solution possible :

```cpp
// C2033b.cpp
// compile with: /c
struct S {
   int b : 1;
};
```
