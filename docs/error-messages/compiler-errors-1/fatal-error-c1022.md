---
title: Erreur irrécupérable C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: 044ebbbe895677acf74977e56879c292486e18cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432563"
---
# <a name="fatal-error-c1022"></a>Erreur irrécupérable C1022

#endif attendu

Une directive `#if`, `#ifdef`ou `#ifndef` n’a aucune directive `#endif` correspondante. Vérifiez que chaque directive `#if`, `#ifdef`ou `#ifndef` a une directive `#endif`correspondante.

L’exemple suivant génère l’erreur C1022 :

```
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Solution possible :

```
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```