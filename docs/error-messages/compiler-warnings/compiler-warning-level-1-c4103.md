---
title: Compilateur avertissement (niveau 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 15d7403d461467e33b7e89957821a311179d33a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577812"
---
# <a name="compiler-warning-level-1-c4103"></a>Compilateur avertissement (niveau 1) C4103

'NomFichier' : alignement modifié après l’en-tête, peut être due à l’absence de #pragma pack(pop)

La compression affecte la disposition des classes, et en général, si la modification de la compression sur les fichiers d’en-tête, il peut y avoir des problèmes.

Utiliser #pragma [pack](../../preprocessor/pack.md)(pop) avant de quitter le fichier d’en-tête pour résoudre cet avertissement.

L’exemple suivant génère l’erreur C4103 :

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

Puis,

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```