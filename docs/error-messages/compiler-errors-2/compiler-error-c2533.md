---
title: Erreur du compilateur C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: b111448e7e9d8260a5101d05996a670013936894
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746407"
---
# <a name="compiler-error-c2533"></a>Erreur du compilateur C2533

’identificateur’ : type de retour non autorisé pour les constructeurs

Un constructeur ne peut pas avoir de type de retour (pas même un type de retour `void`).

Une source courante de cette erreur est un point-virgule manquant entre la fin d'une définition de classe et l'implémentation du premier constructeur. Le compilateur considère la classe comme une définition du type de retour de la fonction constructeur et génère l’erreur C2533.

L'exemple suivant génère l'erreur C2533 et montre comment la corriger :

```cpp
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```
