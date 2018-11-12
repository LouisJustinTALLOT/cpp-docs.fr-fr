---
title: Erreur irrécupérable 1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637903"
---
# <a name="fatal-error-c1311"></a>Erreur irrécupérable 1311

Le format COFF ne peut pas initialiser de manière statique 'var' avec numéro octet (s) d’une adresse

Une adresse dont la valeur n’est pas connue au moment de la compilation ne peut pas être affectée de manière statique à une variable dont le type possède un stockage moins de quatre octets.

Cette erreur peut se produire sur du code qui est sinon C++ valide.

L’exemple suivant montre une condition qui peut générer l’erreur C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```