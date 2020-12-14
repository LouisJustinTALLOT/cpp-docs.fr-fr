---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0032'
title: Erreur de génération de projet PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 25c8f9480e63a8afee23c880912e17632111a4c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241142"
---
# <a name="project-build-error-prj0032"></a>Erreur de génération de projet PRJ0032

La propriété’Outputs’de l’étape de génération personnalisée au niveau du projet contenait’macro', qui donne’macro_expansion'.

Une étape de génération personnalisée sur un projet avait une sortie incorrecte probablement en raison d’un problème d’évaluation de macro. Cette erreur peut également signifier que le chemin d’accès est mal formé, contenant des caractères ou des combinaisons de caractères non conformes dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corrigez la spécification du chemin d’accès. Le chemin d’accès évalué est un chemin d’accès absolu à partir du répertoire du projet.
