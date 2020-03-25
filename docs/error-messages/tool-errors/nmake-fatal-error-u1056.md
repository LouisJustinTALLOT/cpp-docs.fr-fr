---
title: Erreur irrécupérable NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182901"
---
# <a name="nmake-fatal-error-u1056"></a>Erreur irrécupérable NMAKE U1056

Impossible de trouver le processeur de commandes

Le processeur de commandes n’était pas dans le chemin spécifié dans les variables d’environnement **COMSPEC** ou **path** .

NMAKE utilise COMMAND.COM ou CMD. EXE en tant que processeur de commande lors de l’exécution de commandes. Il recherche le processeur de commandes en premier dans le chemin d’accès défini dans **COMSPEC**. Si **COMSPEC** n’existe pas, NMAKE recherche les répertoires spécifiés dans **path**.
