---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4552'
title: Avertissement du compilateur (niveau 1) C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: 52cea1aac8b46fc5c1958bd917f6ab910ef326c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265920"
---
# <a name="compiler-warning-level-1-c4552"></a>Avertissement du compilateur (niveau 1) C4552

'operator' : l’opérateur n’a aucun effet ; opérateur avec effet secondaire ATTENDU

Si une instruction d’expression a un opérateur sans effet secondaire en haut de l’expression, il s’agit probablement d’une erreur.

Pour remplacer cet avertissement, mettez l’expression entre parenthèses.

L’exemple suivant génère l’C4552 :

```cpp
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```
