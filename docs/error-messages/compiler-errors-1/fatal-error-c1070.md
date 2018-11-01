---
title: Erreur irrécupérable C1070
ms.date: 11/04/2016
f1_keywords:
- C1070
helpviewer_keywords:
- C1070
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
ms.openlocfilehash: 7e156a230ce9550b65d1b8775947fc7294c15377
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445017"
---
# <a name="fatal-error-c1070"></a>Erreur irrécupérable C1070

non concordance #if/#endif dans le fichier 'nom_fichier'

Une directive `#if`, `#ifdef`ou `#ifndef` n’a pas de `#endif`correspondant.

L’exemple suivant génère l’erreur C1070 :

```
// C1070.cpp
#define TEST

#ifdef TEST

#ifdef TEST
#endif
// C1070
```

Solution possible :

```
// C1070b.cpp
// compile with: /c
#define TEST

#ifdef TEST
#endif

#ifdef TEST
#endif
```