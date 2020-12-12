---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4172'
title: Avertissement du compilateur (niveau 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7bcfe460150e543c1e3fb6a93ed6656619b5cb13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266934"
---
# <a name="compiler-warning-level-1-c4172"></a>Avertissement du compilateur (niveau 1) C4172

retour de l’adresse d’une variable locale ou temporaire

Une fonction retourne l’adresse d’une variable locale ou d’un objet temporaire. Les variables locales et les objets temporaires sont détruits lorsqu’une fonction est retournée, de sorte que l’adresse retournée n’est pas valide.

Reconcevez la fonction afin qu’elle ne retourne pas l’adresse d’un objet local.

L’exemple suivant génère l’C4172 :

```cpp
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```
