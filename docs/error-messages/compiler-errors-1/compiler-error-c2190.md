---
description: 'En savoir plus sur : erreur du compilateur C2190'
title: Erreur du compilateur C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: aeee732ff819746afa3bc572d4c090a694707afd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337696"
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
