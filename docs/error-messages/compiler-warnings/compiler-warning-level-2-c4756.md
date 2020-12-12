---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4756'
title: Avertissement du compilateur (niveau 2) C4756
ms.date: 11/04/2016
f1_keywords:
- C4756
helpviewer_keywords:
- C4756
ms.assetid: 5a16df83-6b82-4619-83bd-319af4ef1d1d
ms.openlocfilehash: 3031a882feaba0d96adf588481de29431b337ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173452"
---
# <a name="compiler-warning-level-2-c4756"></a>Avertissement du compilateur (niveau 2) C4756

dépassement de capacité arithmétique constante

Le compilateur a généré une exception lors d’une opération arithmétique de constante pendant la compilation.

L’exemple suivant génère l’C4756 :

```cpp
// C4756.cpp
// compile with: /W2 /Od
int main()
{
   float f = 1e100+1e100;   // C4756
}
```
