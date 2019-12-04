---
title: Erreur du compilateur C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: c416c833edf522e4e67cf84aaf7fc945ee8a7972
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755107"
---
# <a name="compiler-error-c2034"></a>Erreur du compilateur C2034

'identificateur' : type de champ de bits trop petit pour le nombre de bits

Le nombre de bits dans la déclaration de champ de bits dépasse la taille du type de base.

L’exemple suivant génère l’C2034 :

```cpp
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

Solution possible :

```cpp
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```
