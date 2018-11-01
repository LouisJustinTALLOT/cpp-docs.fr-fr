---
title: Erreur du compilateur C2156
ms.date: 11/04/2016
f1_keywords:
- C2156
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
ms.openlocfilehash: e2637a54249c37f3872d87959f2cf6d7bf73481e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532572"
---
# <a name="compiler-error-c2156"></a>Erreur du compilateur C2156

pragma doit être à l'extérieur de la fonction

Un pragma qui doit être spécifié à un niveau global (en dehors d’un corps de fonction) se trouve dans une fonction.

L’exemple suivant génère l’erreur C2156 :

```
// C2156.cpp
#pragma optimize( "l", on )   // OK
int main() {
   #pragma optimize( "l", on )   // C2156
}
```