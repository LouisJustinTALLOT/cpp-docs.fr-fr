---
title: Erreur du compilateur C2611
ms.date: 11/04/2016
f1_keywords:
- C2611
helpviewer_keywords:
- C2611
ms.assetid: 3f2d5253-f24f-4724-83d0-6b2aa6a4e551
ms.openlocfilehash: b3c043f8aa8b6fcf4f63e9432e4a1b7222528285
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243308"
---
# <a name="compiler-error-c2611"></a>Erreur du compilateur C2611

'jeton' : non conforme après ' ~' (identificateur attendu)

Le jeton n’est pas un identificateur.

L’exemple suivant génère C2611 :

```
// C2611.cpp
// compile with: /c
class C {
   C::~operator int();   // C2611
   ~C();   // OK
};
```