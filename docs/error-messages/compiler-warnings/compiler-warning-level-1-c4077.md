---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4077'
title: Avertissement du compilateur (niveau 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 96e611db6d36dfa62d96561deb2f4c4d57638c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208708"
---
# <a name="compiler-warning-level-1-c4077"></a>Avertissement du compilateur (niveau 1) C4077

option check_stack inconnue

L’ancienne forme du pragma **check_stack** est utilisée avec un argument inconnu. L’argument doit être `+`, `-`, `(on)`, `(off)`ou vide.

Le compilateur ignore le pragma et laisse le contrôle de pile inchangé.

## <a name="example"></a>Exemple

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```
