---
description: 'En savoir plus sur : erreur du compilateur C2838'
title: Erreur du compilateur C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 70bc1fa038df33cfe63fccd7dc3db8983950b525
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194395"
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
