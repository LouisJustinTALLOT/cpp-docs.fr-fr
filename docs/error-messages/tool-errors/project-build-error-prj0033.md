---
title: Erreur de génération de projet PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: e074ee18508271b56686aa16f9012085ed3bd77d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586210"
---
# <a name="project-build-error-prj0033"></a>Erreur de génération de projet PRJ0033

La propriété 'Dépendances supplémentaires' pour la génération personnalisée étape pour le fichier 'fichier' contenait 'macro' dont l’évaluation donne 'expansion_macro'.

Une étape de génération personnalisée sur un fichier contenait une erreur dans ses dépendances supplémentaires, probablement en raison d’un problème d’évaluation de macros. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corriger la spécification de chemin d’accès. Le chemin d’accès évaluée est un chemin d’accès absolu du répertoire du projet.