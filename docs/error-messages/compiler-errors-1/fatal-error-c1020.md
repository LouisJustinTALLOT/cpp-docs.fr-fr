---
description: 'En savoir plus sur : erreur irrécupérable C1020'
title: Erreur irrécupérable C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: 444da85bddf65533eb5ae37278085664efeae7ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316360"
---
# <a name="fatal-error-c1020"></a>Erreur irrécupérable C1020

#endif inattendu

La directive `#endif` n’a aucune directive `#if`, `#ifdef`ou `#ifndef` correspondante. Vérifiez que chaque `#endif` a une directive correspondante.

L’exemple suivant génère l’erreur C1020 :

```cpp
// C1020.cpp
#endif     // C1020
```

Solution possible :

```cpp
// C1020b.cpp
// compile with: /c
#if 1
#endif
```
