---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4651'
title: Avertissement du compilateur (niveau 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 319d08799ed9494a5ef1d4d7b663fb8ec7b303e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318856"
---
# <a name="compiler-warning-level-1-c4651"></a>Avertissement du compilateur (niveau 1) C4651

'définition’spécifié pour l’en-tête précompilé mais pas pour la compilation actuelle

La définition a été spécifiée lorsque l’en-tête précompilé a été généré, mais pas dans cette compilation.

La définition sera appliquée à l’intérieur de l’en-tête précompilé, mais pas dans le reste du code.

Si un en-tête précompilé a été généré avec/DSYMBOL, le compilateur génère cet avertissement si la compilation/Yu n’a pas/DSYMBOL.  L’ajout de/DSYMBOL à la ligne de commande/Yu résout cet avertissement.
