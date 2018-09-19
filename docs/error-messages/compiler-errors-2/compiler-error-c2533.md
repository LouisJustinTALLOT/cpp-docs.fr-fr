---
title: Erreur du compilateur C2533 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 528b78e71713725907a9f0e2bd06cec1a8c62e67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045404"
---
# <a name="compiler-error-c2533"></a>Erreur du compilateur C2533

’identificateur’ : type de retour non autorisé pour les constructeurs

Un constructeur ne peut pas avoir de type de retour (pas même un type de retour `void`).

Une source courante de cette erreur est un point-virgule manquant entre la fin d'une définition de classe et l'implémentation du premier constructeur. Le compilateur considère la classe comme une définition du type de retour de la fonction constructeur et génère l'erreur C2533.

L'exemple suivant génère l'erreur C2533 et montre comment la corriger :

```
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```