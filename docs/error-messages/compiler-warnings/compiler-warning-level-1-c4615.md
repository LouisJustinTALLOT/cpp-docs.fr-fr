---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4615'
title: Avertissement du compilateur (niveau 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 174ffa81e9f5927833b877ede7cf24ae530b94fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339218"
---
# <a name="compiler-warning-level-1-c4615"></a>Avertissement du compilateur (niveau 1) C4615

\#pragma warning : type d’avertissement utilisateur inconnu

Un spécificateur d’avertissement non valide a été utilisé avec l' [Avertissement](../../preprocessor/warning.md) **pragma** . Pour résoudre l’erreur, utilisez un spécificateur d’avertissement valide.

L’exemple suivant génère l’C4615 :

```cpp
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```
