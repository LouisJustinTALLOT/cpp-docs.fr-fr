---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4619'
title: Avertissement du compilateur (niveau 3) C4619
ms.date: 11/04/2016
f1_keywords:
- C4619
helpviewer_keywords:
- C4619
ms.assetid: 701fea21-01aa-4bea-93d4-1cb8824170b0
ms.openlocfilehash: c108e4d1a0845cc6629a36307c33fc8342cadd67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337269"
---
# <a name="compiler-warning-level-3-c4619"></a>Avertissement du compilateur (niveau 3) C4619

\#pragma warning : il n’y a aucun numéro d’avertissement’Number'

Une tentative de désactivation d’un avertissement qui n’existe pas a été effectuée.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4619 :

```cpp
// C4619.cpp
// compile with: /W3 /c
#pragma warning(default : 4619)
#pragma warning(disable : 4354)   // C4619, C4354 does not exist
```
