---
title: Erreur du compilateur C2156
ms.date: 11/04/2016
f1_keywords:
- C2156
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
ms.openlocfilehash: e2637a54249c37f3872d87959f2cf6d7bf73481e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174885"
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