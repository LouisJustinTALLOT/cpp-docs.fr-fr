---
title: Erreur du compilateur C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 168f45a8cca8591d4780d056403de70440d25bec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757837"
---
# <a name="compiler-error-c2838"></a>Erreur du compilateur C2838

'membre' : nom qualifié non conforme dans une déclaration de membre

Une classe, une structure ou une Union utilise un nom qualifié complet pour redéclarer un membre d’une autre classe, structure ou Union.

L’exemple suivant génère l’C2838 :

```cpp
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
