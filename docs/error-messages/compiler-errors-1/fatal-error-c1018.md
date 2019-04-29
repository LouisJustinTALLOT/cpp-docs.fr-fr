---
title: Erreur irrécupérable C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383215"
---
# <a name="fatal-error-c1018"></a>Erreur irrécupérable C1018

#elif inattendu

La directive `#elif` se trouve à l’extérieur d’une construction `#if`, `#ifdef`ou `#ifndef` . Utilisez `#elif` uniquement dans l’une de ces constructions.

L’exemple suivant génère l’erreur C1018 :

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

Solution possible :

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```