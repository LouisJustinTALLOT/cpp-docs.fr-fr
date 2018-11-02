---
title: Erreur du compilateur C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501658"
---
# <a name="compiler-error-c3161"></a>Erreur du compilateur C3161

'interface' : classe d’imbrication, struct, union ou interface dans une interface n’est pas conforme ; imbrication d’une interface dans une classe, struct ou une union n’est pas conforme

Un [__interface](../../cpp/interface.md) peut uniquement apparaître dans une portée globale ou au sein d’un espace de noms. Une classe, un struct ou une union ne peut pas apparaître dans une interface.

## <a name="example"></a>Exemple

L’exemple suivant génère C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```