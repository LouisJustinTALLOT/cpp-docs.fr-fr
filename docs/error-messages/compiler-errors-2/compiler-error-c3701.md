---
description: 'En savoir plus sur : erreur du compilateur C3701'
title: Erreur du compilateur C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: 8ebc8ac41091770a59876fb829d86997d7f5709c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228688"
---
# <a name="compiler-error-c3701"></a>Erreur du compilateur C3701

'fonction' : event_source n’a pas d’événements

Vous avez tenté d’utiliser [event_source](../../windows/attributes/event-source.md) sur une classe qui n’a pas de méthodes d’événement. Pour corriger cette erreur, ajoutez un ou plusieurs événements à la classe.

L’exemple suivant génère l’C3701 :

```cpp
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
