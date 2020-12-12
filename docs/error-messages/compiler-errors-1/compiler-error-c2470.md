---
description: 'En savoir plus sur : erreur du compilateur C2470'
title: Erreur du compilateur C2470
ms.date: 11/04/2016
f1_keywords:
- C2470
helpviewer_keywords:
- C2470
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
ms.openlocfilehash: 90a57f02022044aca7b4062ea287eae213c26f74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164508"
---
# <a name="compiler-error-c2470"></a>Erreur du compilateur C2470

'fonction' : similaire à une définition de fonction, mais il n’existe aucune liste de paramètres ; corps apparent ignoré

Il manque une liste d’arguments dans une définition de fonction.

L’exemple suivant génère l’C2470 :

```cpp
// C2470.cpp
int MyFunc {};  // C2470
void MyFunc2() {};  //OK

int main(){
   MyFunc();
   MyFunc2();
}
```
