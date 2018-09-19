---
title: Erreur irrécupérable NMAKE U1064 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092997"
---
# <a name="nmake-fatal-error-u1064"></a>Erreur irrécupérable NMAKE U1064

MAKEFILE introuvable et aucune cible spécifiée

La ligne de commande NMAKE ne spécifiait pas un makefile ou une cible, et le répertoire actif ne contenait pas d’un fichier nommé MAKEFILE.

NMAKE exige un makefile ou une cible de ligne de commande (ou les deux). Pour rendre un makefile NMAKE, spécifiez l’option /F ou placez un fichier nommé MAKEFILE dans le répertoire actif. NMAKE peut créer une cible de ligne de commande à l’aide d’une règle d’inférence si un makefile n’est pas fourni.