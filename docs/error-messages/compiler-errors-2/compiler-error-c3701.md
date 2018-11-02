---
title: Erreur du compilateur C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: 2efbf3c48b7c366d262facac9cebb4f72d9f1513
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580596"
---
# <a name="compiler-error-c3701"></a>Erreur du compilateur C3701

'fonction' : event_source n’a aucun événement

Vous avez tenté d’utiliser [event_source](../../windows/event-source.md) sur une classe qui ne possède aucune méthode d’événement. Pour corriger cette erreur, ajoutez un ou plusieurs événements à la classe.

L’exemple suivant génère l’erreur C3701 :

```
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```