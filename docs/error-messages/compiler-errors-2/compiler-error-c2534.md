---
description: 'En savoir plus sur : erreur du compilateur C2534'
title: Erreur du compilateur C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: fbdc4c292a8eb59ee9ab51de0100455139473f7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302073"
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
