---
title: Avertissement du compilateur (niveau 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199540"
---
# <a name="compiler-warning-level-1-c4651"></a>Avertissement du compilateur (niveau 1) C4651

'définition’spécifié pour l’en-tête précompilé mais pas pour la compilation actuelle

La définition a été spécifiée lorsque l’en-tête précompilé a été généré, mais pas dans cette compilation.

La définition sera appliquée à l’intérieur de l’en-tête précompilé, mais pas dans le reste du code.

Si un en-tête précompilé a été généré avec/DSYMBOL, le compilateur génère cet avertissement si la compilation/Yu n’a pas/DSYMBOL.  L’ajout de/DSYMBOL à la ligne de commande/Yu résout cet avertissement.
