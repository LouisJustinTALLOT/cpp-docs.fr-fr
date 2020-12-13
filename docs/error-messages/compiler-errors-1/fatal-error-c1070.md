---
description: 'En savoir plus sur : erreur irrécupérable C1070'
title: Erreur irrécupérable C1070
ms.date: 11/04/2016
f1_keywords:
- C1070
helpviewer_keywords:
- C1070
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
ms.openlocfilehash: 2668bfa6c24c602606cbd9ee41b5322272eec093
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344391"
---
# <a name="fatal-error-c1070"></a>Erreur irrécupérable C1070

non concordance #if/#endif dans le fichier 'nom_fichier'

Une directive `#if`, `#ifdef`ou `#ifndef` n’a pas de `#endif`correspondant.

L’exemple suivant génère l’erreur C1070 :

```cpp
// C1070.cpp
#define TEST

#ifdef TEST

#ifdef TEST
#endif
// C1070
```

Solution possible :

```cpp
// C1070b.cpp
// compile with: /c
#define TEST

#ifdef TEST
#endif

#ifdef TEST
#endif
```
