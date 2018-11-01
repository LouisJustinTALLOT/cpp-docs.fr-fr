---
title: Erreur du compilateur C2192
ms.date: 11/04/2016
f1_keywords:
- C2192
helpviewer_keywords:
- C2192
ms.assetid: a147197e-e72d-4620-939b-f9e08d7c7c12
ms.openlocfilehash: 3285221089c2a1ed61b03572ed8915ebfbb00e48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444250"
---
# <a name="compiler-error-c2192"></a>Erreur du compilateur C2192

déclaration du paramètre 'nombre' différente

Une fonction C a été déclarée une deuxième fois avec une liste de paramètres différente. C ne prend pas en charge les fonctions surchargées.

L’exemple suivant génère l’erreur C2192 :

```
// C2192.c
// compile with: /Za /c
void func( float, int );
void func( int, float );   // C2192, different parameter list
void func2( int, float );   // OK
```