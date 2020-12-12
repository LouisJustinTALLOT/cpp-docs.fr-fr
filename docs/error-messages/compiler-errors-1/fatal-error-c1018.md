---
description: 'En savoir plus sur : erreur irrécupérable C1018'
title: Erreur irrécupérable C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 68b81406916ef358a73112c9f6f8b2370c627e54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316412"
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
