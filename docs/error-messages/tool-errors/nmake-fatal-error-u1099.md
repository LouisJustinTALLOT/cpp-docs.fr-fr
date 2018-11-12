---
title: Erreur irrécupérable NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631216"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099

dépassement de capacité de la pile

Le makefile en cours de traitement était trop complexe pour la taille de la pile dans NMAKE. NMAKE a une allocation de 0 x 3000 (12 Ko).

Pour augmenter l’allocation de piles de NMAKE, exécutez le [editbin /stack](../../build/reference/stack.md) utilitaire avec une option de pile plus importante :

**EDITBIN /STACK:reserve NMAKE. EXE**

où *réserver* est un nombre supérieur à l’allocation de pile en cours dans NMAKE.