---
title: Erreur de génération de projet PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: f1f292f3979c993a8fa8cb8ff44653ac7124b121
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344345"
---
# <a name="project-build-error-prj0032"></a>Erreur de génération de projet PRJ0032

La propriété 'Sorties' de l’étape de génération personnalisée au niveau du projet contenait 'macro', dont l’évaluation donne 'expansion_macro'.

Une étape de génération personnalisée sur un projet avait un résultat erroné probablement en raison d’un problème d’évaluation de macros. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corriger la spécification de chemin d’accès. Le chemin d’accès évaluée est un chemin d’accès absolu du répertoire du projet.