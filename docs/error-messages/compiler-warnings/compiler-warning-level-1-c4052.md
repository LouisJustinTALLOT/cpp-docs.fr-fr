---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4052'
title: Avertissement du compilateur (niveau 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 0da0823b3268e8f957a87d1c975fb82098fe2511
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160556"
---
# <a name="compiler-warning-level-1-c4052"></a>Avertissement du compilateur (niveau 1) C4052

déclarations de fonction différentes, une seule contient des arguments de variables

L’une des déclarations de la fonction ne contient pas d’arguments de variables. Elle est ignorée.

L’exemple suivant génère l’avertissement C4052 :

```c
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```
