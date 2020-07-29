---
title: Erreur du compilateur C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 202e3bbe2238b4cc2a5233ac4e093717d623f099
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207899"
---
# <a name="compiler-error-c2534"></a>Erreur du compilateur C2534

'identificateur' : le constructeur ne peut pas retourner de valeur

Un constructeur ne peut pas retourner de valeur ou avoir un type de retour (pas même un **`void`** type de retour).

Cette erreur peut être corrigée en supprimant l' **`return`** instruction de la définition du constructeur.

L’exemple suivant génère l’C2534 :

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
