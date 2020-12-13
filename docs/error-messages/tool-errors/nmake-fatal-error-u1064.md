---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1064'
title: Erreur irrécupérable NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 881c93eca4efad064dff633bbde34dc88e71345e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330365"
---
# <a name="nmake-fatal-error-u1064"></a>Erreur irrécupérable NMAKE U1064

MAKEFILE introuvable et aucune cible spécifiée

La ligne de commande NMAKE n’a pas spécifié de Makefile ou de cible et le répertoire actif ne contenait pas de fichier MAKEFILE.

NMAKE requiert un Makefile ou une cible de ligne de commande (ou les deux). Pour rendre un Makefile disponible pour NMAKE, spécifiez l’option/F ou placez un fichier nommé MAKEFILE dans le répertoire actif. NMAKE peut créer une cible de ligne de commande à l’aide d’une règle d’inférence si aucun Makefile n’est fourni.
