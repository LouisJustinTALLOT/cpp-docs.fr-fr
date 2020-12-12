---
description: 'En savoir plus sur : erreur du compilateur C3704'
title: Erreur du compilateur C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: aae489b2d8657a1e62adc654d148be6cd0403af1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278179"
---
# <a name="compiler-error-c3704"></a>Erreur du compilateur C3704

'fonction' : une méthode vararg ne peut pas déclencher d’événements

Vous avez tenté d’utiliser [__event](../../cpp/event.md) sur une méthode vararg. Pour corriger cette erreur, remplacez l' `fireEvent(int i, ...)` appel par l' `fireEvent(int i)` appel comme indiqué dans l’exemple de code suivant.

L’exemple suivant génère l’C3704 :

```cpp
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```
