---
title: Erreur irrécupérable NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367263"
---
# <a name="nmake-fatal-error-u1056"></a>Erreur irrécupérable NMAKE U1056

Impossible de trouver le processeur de commandes

Le processeur de commandes n’était pas dans le chemin d’accès spécifié dans le **COMSPEC** ou **chemin d’accès** variables d’environnement.

NMAKE utilise COMMAND.COM ou CMD. EXE en tant qu’interpréteur de commandes lors de l’exécution de commandes. Il recherche l’interpréteur de commandes dans le chemin d’accès défini **COMSPEC**. Si **COMSPEC** n’existe pas, les répertoires spécifiés dans des recherches NMAKE **chemin d’accès**.