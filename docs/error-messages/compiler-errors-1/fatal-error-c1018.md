---
title: Erreur irrécupérable C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532656"
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

Résolution possible :

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```