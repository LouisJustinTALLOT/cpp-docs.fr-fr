---
title: Erreur du compilateur C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 7970ba5d8d2b19bd6e330fad1879880fc5cbf32d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516942"
---
# <a name="compiler-error-c2208"></a>Erreur du compilateur C2208

'type' : aucun membre défini à l’aide de ce type

Un identificateur résolu en un nom de type est dans une déclaration globale, mais le compilateur ne peut pas déclarer un membre.

L’exemple suivant génère l’erreur C2208 :

```
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```