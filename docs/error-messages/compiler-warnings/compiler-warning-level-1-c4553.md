---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4553'
title: Avertissement du compilateur (niveau 1) C4553
ms.date: 11/04/2016
f1_keywords:
- C4553
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
ms.openlocfilehash: 93d775e1a91f8306240824f99da1fae107963696
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265894"
---
# <a name="compiler-warning-level-1-c4553"></a>Avertissement du compilateur (niveau 1) C4553

'operator' : l’opérateur n’a aucun effet ; souhaitiez-vous’operator' ?

Si une instruction d’expression a un opérateur sans effet secondaire en haut de l’expression, il s’agit probablement d’une erreur.

L’exemple suivant génère l’C4553 :

```cpp
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```
