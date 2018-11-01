---
title: Avertissement du compilateur (niveau 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: c7d2a603b7ec97889b075c7a67e5b8439ad487af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599626"
---
# <a name="compiler-warning-level-1-c4052"></a>Avertissement du compilateur (niveau 1) C4052

déclarations de fonction différentes, une seule contient des arguments de variables

L’une des déclarations de la fonction ne contient pas d’arguments de variables. Elle est ignorée.

L’exemple suivant génère l’avertissement C4052 :

```
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```