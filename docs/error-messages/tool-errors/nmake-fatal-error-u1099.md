---
title: Erreur irrécupérable NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298241"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099

dépassement de capacité de la pile

Le makefile en cours de traitement était trop complexe pour la taille de la pile dans NMAKE. NMAKE a une allocation de 0 x 3000 (12 Ko).

Pour augmenter l’allocation de piles de NMAKE, exécutez le [editbin /stack](../../build/reference/stack.md) utilitaire avec une option de pile plus importante :

**EDITBIN /STACK:reserve NMAKE. EXE**

où *réserver* est un nombre supérieur à l’allocation de pile en cours dans NMAKE.