---
title: Compilateur avertissement (niveau 1) C4052 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67e63f694a190a3d7c694fa99ff0433870a1b9c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103399"
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