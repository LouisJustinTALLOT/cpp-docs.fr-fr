---
title: Erreur du compilateur C2751
ms.date: 11/04/2016
f1_keywords:
- C2751
helpviewer_keywords:
- C2751
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
ms.openlocfilehash: 7b9d8ca4acbbda011cdfa7a467cbb8323dcc7cc5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759592"
---
# <a name="compiler-error-c2751"></a>Erreur du compilateur C2751

'paramètre' : le nom d’un paramètre de fonction ne peut pas être qualifié

Vous ne pouvez pas utiliser un nom qualifié en tant que paramètre de fonction.

L’exemple suivant génère l’C2751 :

```cpp
// C2751.cpp
namespace std {
   template<typename T>
   class list {};
}

#define list std::list
void f(int &list){}   // C2751
```
