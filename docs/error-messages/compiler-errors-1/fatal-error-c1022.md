---
title: Erreur irrécupérable C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: b709d4bd855e38cb3721dec6d09b95ed02454def
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756875"
---
# <a name="fatal-error-c1022"></a>Erreur irrécupérable C1022

#endif attendu

Une directive `#if`, `#ifdef`ou `#ifndef` n’a aucune directive `#endif` correspondante. Vérifiez que chaque directive `#if`, `#ifdef`ou `#ifndef` a une directive `#endif`correspondante.

L’exemple suivant génère l’erreur C1022 :

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Solution possible :

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
