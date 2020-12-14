---
description: 'En savoir plus sur : erreur irrécupérable C1022'
title: Erreur irrécupérable C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: cd608aded29b4f3ebf329586ebc03ce2e325c970
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249761"
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
