---
title: Erreur irrécupérable C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 3273288f1d60fad840fd8e9c459ce5d209ddb6a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756927"
---
# <a name="fatal-error-c1018"></a>Erreur irrécupérable C1018

#elif inattendu

La directive `#elif` se trouve à l’extérieur d’une construction `#if`, `#ifdef`ou `#ifndef` . Utilisez `#elif` uniquement dans l’une de ces constructions.

L’exemple suivant génère l’erreur C1018 :

```cpp
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

Solution possible :

```cpp
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```
