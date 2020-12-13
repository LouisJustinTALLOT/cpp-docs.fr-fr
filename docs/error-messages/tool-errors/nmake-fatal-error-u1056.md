---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1056'
title: Erreur irrécupérable NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: beb7814d2e29665e1f92c7ef1e8dadbd66af5d63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330379"
---
# <a name="nmake-fatal-error-u1056"></a>Erreur irrécupérable NMAKE U1056

Impossible de trouver le processeur de commandes

Le processeur de commandes n’était pas dans le chemin spécifié dans les variables d’environnement **COMSPEC** ou **path** .

NMAKE utilise COMMAND.COM ou CMD.EXE en tant que processeur de commandes lors de l’exécution de commandes. Il recherche le processeur de commandes en premier dans le chemin d’accès défini dans **COMSPEC**. Si **COMSPEC** n’existe pas, NMAKE recherche les répertoires spécifiés dans **path**.
