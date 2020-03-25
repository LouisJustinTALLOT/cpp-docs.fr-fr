---
title: Avertissement du compilateur (niveau 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7258172c00b1ff4aebb18fa2c715559fd82a2180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163544"
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
