---
title: Erreur du compilateur C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 1482efa8b018914a4ebc509464622726ae9ebb20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560379"
---
# <a name="compiler-error-c2838"></a>Erreur du compilateur C2838

'membre' : nom qualifié non conforme dans une déclaration de membre

Une classe, une structure ou une union utilise un nom qualifié complet pour redéclarer un membre d’une autre classe, structure ou union.

L’exemple suivant génère l’erreur C2838 :

```
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```