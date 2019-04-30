---
title: Erreur du compilateur C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: 447869b029df41219f71dcc633e9ae8a3934e0ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408483"
---
# <a name="compiler-error-c2570"></a>Erreur du compilateur C2570

'identificateur' : union ne peut pas avoir de classes de base

Une union dérive d’une classe, une structure ou une union. Cette opération n’est pas autorisée. Déclarez le type dérivé en tant que classe ou structure à la place.

L’exemple suivant génère l’erreur C2570 :

```
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```