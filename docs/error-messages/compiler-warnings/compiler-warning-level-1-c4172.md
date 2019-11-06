---
title: Avertissement du compilateur (niveau 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7d53972dbcb2e3ab6a95b0b874cc6bb98cd66840
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624828"
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