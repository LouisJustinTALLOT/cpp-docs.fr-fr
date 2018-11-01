---
title: Erreur irrécupérable C1019
ms.date: 11/04/2016
f1_keywords:
- C1019
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
ms.openlocfilehash: 2d8e63510b762b0de0cda50ab7a03b773dfb949a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574081"
---
# <a name="fatal-error-c1019"></a>Erreur irrécupérable C1019

#else inattendu

La directive `#else` se trouve à l’extérieur d’une construction `#if`, `#ifdef`ou `#ifndef` . Utilisez `#else` uniquement dans l’une de ces constructions.

L’exemple suivant génère l’erreur C1019 :

```
// C1019.cpp
#else   // C1019
#endif

int main() {}
```

Solution possible :

```
// C1019b.cpp
#if 1
#else
#endif

int main() {}
```