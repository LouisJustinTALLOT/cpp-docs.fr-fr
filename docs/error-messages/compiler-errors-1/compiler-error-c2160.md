---
title: Erreur du compilateur C2160
ms.date: 11/04/2016
f1_keywords:
- C2160
helpviewer_keywords:
- C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
ms.openlocfilehash: 0cfc0822ab790a456c6fa56142047c1826257477
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740856"
---
# <a name="compiler-error-c2160"></a>Erreur du compilateur C2160

'##' ne peut se trouver au début de la définition d'une macro

La définition d’une macro a commencé par un opérateur de collage de jeton (##).

L’exemple suivant génère l’erreur C2160 :

```cpp
// C2160.cpp
// compile with: /c
#define mac(a,b) #a   // OK
#define mac(a,b) ##a   // C2160
```
