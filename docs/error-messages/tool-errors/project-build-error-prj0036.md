---
title: Erreur de génération de projet PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 9b9232583c464548167e22d0104e0c6098093eab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348391"
---
# <a name="project-build-error-prj0036"></a>Erreur de génération de projet PRJ0036

La propriété 'Fichiers supplémentaires' de l’outil de déploiement Web contenait une entrée non valide.

La propriété des fichiers supplémentaires sur la page de propriétés de déploiement Web contenait une erreur, probablement en raison d’un problème d’évaluation de macros. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corriger la spécification de chemin d’accès. Le chemin d’accès évaluée est un chemin d’accès absolu du répertoire du projet.

Cette erreur peut aussi signifier qu’un des fichiers référencés n’existe pas.