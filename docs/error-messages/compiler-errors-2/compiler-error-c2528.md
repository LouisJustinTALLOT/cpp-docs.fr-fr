---
title: Erreur du compilateur C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: f8712cfbd34e852cf852cf9758446849d75d8bdc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756264"
---
# <a name="compiler-error-c2528"></a>Erreur du compilateur C2528

'nom' : pointeur non conforme vers la référence

Vous ne pouvez pas déclarer un pointeur vers une référence. Déréférencez la variable avant de déclarer un pointeur vers celle-ci.

L’exemple suivant génère l’C2528 :

```cpp
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```
