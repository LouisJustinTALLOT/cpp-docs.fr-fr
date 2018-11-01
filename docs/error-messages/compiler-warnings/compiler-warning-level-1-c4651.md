---
title: Avertissement du compilateur (niveau 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434773"
---
# <a name="compiler-warning-level-1-c4651"></a>Avertissement du compilateur (niveau 1) C4651

« définition » spécifiée pour l’en-tête précompilé mais non pour la compilation actuelle

La définition a été spécifiée lors de l’en-tête précompilé a été généré, mais pas dans cette compilation.

La définition sera appliquée à l’intérieur de l’en-tête précompilé, mais pas dans le reste du code.

Si un en-tête précompilé a été généré avec/DSYMBOL, le compilateur génère cet avertissement si la compilation /Yu ne comprend pas /DSYMBOL.  Ajout de /DSYMBOL à la ligne de commande /Yu résout cet avertissement.