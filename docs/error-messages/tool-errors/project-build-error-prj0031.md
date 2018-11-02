---
title: Erreur de génération de projet PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e5edae0c1b7464e4a3a5e9523332ce956d0dcf92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648589"
---
# <a name="project-build-error-prj0031"></a>Erreur de génération de projet PRJ0031

La propriété 'Sorties' de la génération personnalisée étape pour le fichier 'fichier' contenait 'macro' dont l’évaluation donne 'expansion_macro'.

Une étape de génération personnalisée sur un fichier avait un résultat erroné probablement en raison d’un problème d’évaluation de macros. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corriger la spécification de chemin d’accès. Le chemin d’accès évaluée est un chemin d’accès absolu du répertoire du projet.