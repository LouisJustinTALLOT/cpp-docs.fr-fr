---
title: Erreur irrécupérable NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: bfc42c458c1932287f17f367d09c4b23c2c201a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182823"
---
# <a name="nmake-fatal-error-u1064"></a>Erreur irrécupérable NMAKE U1064

MAKEFILE introuvable et aucune cible spécifiée

La ligne de commande NMAKE n’a pas spécifié de Makefile ou de cible et le répertoire actif ne contenait pas de fichier MAKEFILE.

NMAKE requiert un Makefile ou une cible de ligne de commande (ou les deux). Pour rendre un Makefile disponible pour NMAKE, spécifiez l’option/F ou placez un fichier nommé MAKEFILE dans le répertoire actif. NMAKE peut créer une cible de ligne de commande à l’aide d’une règle d’inférence si aucun Makefile n’est fourni.
