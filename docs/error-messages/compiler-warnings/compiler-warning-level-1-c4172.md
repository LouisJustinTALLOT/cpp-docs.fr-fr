---
title: Compilateur avertissement (niveau 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: caa71da9182c1da1d17d87d901084d0ee9badf73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536616"
---
# <a name="compiler-warning-level-1-c4172"></a>Compilateur avertissement (niveau 1) C4172

Retourne l’adresse de variable locale ou temporaire

Une fonction retourne l’adresse d’un objet temporaire ou de variable local. Variables locales et des objets temporaires sont détruits quand une fonction est retournée, l’adresse retournée n’est pas valide.

Remaniez la fonction afin qu’elle ne retourne pas l’adresse d’un objet local.

L’exemple suivant génère l’erreur C4172 :

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```