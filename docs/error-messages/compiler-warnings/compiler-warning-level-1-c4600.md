---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4600'
title: Avertissement du compilateur (niveau 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: d09aff9137647543cd3e71c0fa1794b37fac83f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341774"
---
# <a name="compiler-warning-level-1-c4600"></a>Avertissement du compilateur (niveau 1) C4600

\#pragma’macro Name' : chaîne non vide valide attendue

Vous ne pouvez pas spécifier une chaîne vide quand vous effectuez un push ou un pop sur un nom de macro avec l' [pop_macro](../../preprocessor/pop-macro.md) ou [push_macro](../../preprocessor/push-macro.md).

L’exemple suivant génère l’C4600 :

```cpp
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```
