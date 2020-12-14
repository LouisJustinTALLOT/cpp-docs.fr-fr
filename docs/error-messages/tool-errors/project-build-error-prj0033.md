---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0033'
title: Erreur de génération de projet PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 7faf69cd9aaed6f90d9c546c4fc2383fd6808419
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241129"
---
# <a name="project-build-error-prj0033"></a>Erreur de génération de projet PRJ0033

La propriété’dépendances supplémentaires’de l’étape de génération personnalisée du fichier’fichier’contenait’macro', dont l’évaluation donne’macro_expansion'.

Une étape de génération personnalisée sur un fichier contenait une erreur dans ses dépendances supplémentaires, probablement en raison d’un problème d’évaluation de macro. Cette erreur peut également signifier que le chemin d’accès est mal formé, contenant des caractères ou des combinaisons de caractères non conformes dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corrigez la spécification du chemin d’accès. Le chemin d’accès évalué est un chemin d’accès absolu à partir du répertoire du projet.
