---
description: 'En savoir plus sur : erreur du compilateur C2459'
title: Erreur du compilateur C2459
ms.date: 11/04/2016
f1_keywords:
- C2459
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
ms.openlocfilehash: 35cd97b93a7095aedc0015e2e7d9910172425263
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341865"
---
# <a name="compiler-error-c2459"></a>Erreur du compilateur C2459

'identificateur' : est en cours de définition ; Impossible d’ajouter en tant que membre anonyme

Une classe, une structure ou une Union est redéfinie dans sa propre portée par un membre d’une Union anonyme.

L’exemple suivant génère l’C2459 :

```cpp
// C2459.cpp
// compile with: /c
class C {
   union { int C; };   // C2459
   union { int D; };
};
```
