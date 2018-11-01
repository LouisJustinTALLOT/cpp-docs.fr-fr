---
title: Erreur du compilateur C2110
ms.date: 11/04/2016
f1_keywords:
- C2110
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
ms.openlocfilehash: b20e68ec032abdfae9afb1c94fed064010275149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646964"
---
# <a name="compiler-error-c2110"></a>Erreur du compilateur C2110

'+' : impossible d’ajouter deux pointeurs

L’utilisateur a tenté d’ajouter deux valeurs de pointeur avec l’opérateur `+` (signe plus).

L’exemple suivant génère l’erreur C2110 :

```
// C2110.cpp
int main() {
   int a = 0;
   int *pa;
   int *pb;
   a = pa + pb;   // C2110
}
```