---
title: Avertissement du compilateur (niveau 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: fcfefd5b858df653551e7f3061a41d168c8ff3f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397222"
---
# <a name="compiler-warning-level-1-c4600"></a>Avertissement du compilateur (niveau 1) C4600

\#pragma 'nom_macro' : chaîne valide non vide attendue

Vous ne pouvez pas spécifier une chaîne vide lorsque vous effectuez un push ou pop sur un nom de macro avec le [pop_macro](../../preprocessor/pop-macro.md) ou [push_macro](../../preprocessor/push-macro.md).

L’exemple suivant génère l’erreur C4600 :

```
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```