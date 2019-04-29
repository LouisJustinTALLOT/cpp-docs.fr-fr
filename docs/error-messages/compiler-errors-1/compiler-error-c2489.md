---
title: Erreur du compilateur C2489
ms.date: 11/04/2016
f1_keywords:
- C2489
helpviewer_keywords:
- C2489
ms.assetid: 67d8cd98-db7e-4f7f-86b4-4af7bc89ec8b
ms.openlocfilehash: e4024455e17956fc67917e92a3ca531eca5c5e04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361033"
---
# <a name="compiler-error-c2489"></a>Erreur du compilateur C2489

'identificateur' : variable ou initialisée automatiquement register n’est ne pas autorisée à portée de la fonction d’une fonction 'naked'

Pour plus d’informations, consultez [naked](../../cpp/naked-cpp.md).

L’exemple suivant génère l’erreur C2489 :

```
// C2489.cpp
// processor: x86
__declspec( naked ) int func() {
   int i = 1;   // C2489
   register int j = 1;   // C2489
}
```