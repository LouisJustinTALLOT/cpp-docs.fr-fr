---
title: Erreur de génération de projet PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192495"
---
# <a name="project-build-error-prj0031"></a>Erreur de génération de projet PRJ0031

La propriété’sorties’de l’étape de génération personnalisée du fichier’fichier’contenait’macro', dont l’évaluation correspond à’macro_expansion'.

La sortie d’une étape de génération personnalisée sur un fichier est probablement incorrecte en raison d’un problème d’évaluation de macro. Cette erreur peut également signifier que le chemin d’accès est mal formé, contenant des caractères ou des combinaisons de caractères non conformes dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corrigez la spécification du chemin d’accès. Le chemin d’accès évalué est un chemin d’accès absolu à partir du répertoire du projet.
