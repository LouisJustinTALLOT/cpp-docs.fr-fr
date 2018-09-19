---
title: Erreur irrécupérable NMAKE U1056 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065690"
---
# <a name="nmake-fatal-error-u1056"></a>Erreur irrécupérable NMAKE U1056

Impossible de trouver le processeur de commandes

Le processeur de commandes n’était pas dans le chemin d’accès spécifié dans le **COMSPEC** ou **chemin d’accès** variables d’environnement.

NMAKE utilise COMMAND.COM ou CMD. EXE en tant qu’interpréteur de commandes lors de l’exécution de commandes. Il recherche l’interpréteur de commandes dans le chemin d’accès défini **COMSPEC**. Si **COMSPEC** n’existe pas, les répertoires spécifiés dans des recherches NMAKE **chemin d’accès**.