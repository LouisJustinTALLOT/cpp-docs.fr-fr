---
title: Erreur du compilateur C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: 027c7f49b361ef3aa06a4d74e10f0ff27331b4a9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301884"
---
# <a name="compiler-error-c2190"></a>Erreur du compilateur C2190

première liste de paramètres plus longue que la seconde

Une fonction C a été déclarée une deuxième fois avec une liste de paramètres plus petite. C ne prend pas en charge les fonctions surchargées.

L’exemple suivant génère l’C2190 :

```c
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```
