---
title: Erreur du compilateur C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 6c598c2c5b3ac6d88fb843534cae240c65a2d322
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207912"
---
# <a name="compiler-error-c2533"></a>Erreur du compilateur C2533

’identificateur’ : type de retour non autorisé pour les constructeurs

Un constructeur ne peut pas avoir de type de retour (pas même un **`void`** type de retour).

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
