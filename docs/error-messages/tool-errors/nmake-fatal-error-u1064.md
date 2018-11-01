---
title: Erreur irrécupérable NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463360"
---
# <a name="nmake-fatal-error-u1064"></a>Erreur irrécupérable NMAKE U1064

MAKEFILE introuvable et aucune cible spécifiée

La ligne de commande NMAKE ne spécifiait pas un makefile ou une cible, et le répertoire actif ne contenait pas d’un fichier nommé MAKEFILE.

NMAKE exige un makefile ou une cible de ligne de commande (ou les deux). Pour rendre un makefile NMAKE, spécifiez l’option /F ou placez un fichier nommé MAKEFILE dans le répertoire actif. NMAKE peut créer une cible de ligne de commande à l’aide d’une règle d’inférence si un makefile n’est pas fourni.