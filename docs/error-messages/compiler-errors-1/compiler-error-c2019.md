---
title: Erreur du compilateur C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 6e9e5bbca5da13fdfd4727d3b19aa3656689ce96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531831"
---
# <a name="compiler-error-c2019"></a>Erreur du compilateur C2019

directive du préprocesseur attendue, 'caractère' rencontré

Le caractère suit un `#` connexion, mais il n’est pas la première lettre d’une directive de préprocesseur.

L’exemple suivant génère l’erreur C2019 :

```
// C2019.cpp
#!define TRUE 1   // C2019
```

Solution possible :

```
// C2019b.cpp
// compile with: /c
#define TRUE 1
```