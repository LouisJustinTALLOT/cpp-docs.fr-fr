---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0034'
title: Erreur de génération de projet PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: a5eb76b5a11cfed0789f6f5e5aca52e8215f4c5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241064"
---
# <a name="project-build-error-prj0034"></a>Erreur de génération de projet PRJ0034

La propriété’dépendances supplémentaires’de l’étape de génération personnalisée au niveau du projet contenait’macro', qui donne’macro_expansion'.

Une étape de génération personnalisée sur un projet contenait une erreur dans ses dépendances supplémentaires probablement en raison d’un problème d’évaluation de macro. Cette erreur peut également signifier que le chemin d’accès est mal formé, contenant des caractères ou des combinaisons de caractères non conformes dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corrigez la spécification du chemin d’accès. Le chemin d’accès évalué est un chemin d’accès absolu à partir du répertoire du projet.
