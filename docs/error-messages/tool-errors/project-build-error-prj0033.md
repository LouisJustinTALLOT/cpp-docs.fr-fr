---
title: Erreur de génération PRJ0033 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c70bd942123c48866c3353443b478de4953668de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036070"
---
# <a name="project-build-error-prj0033"></a>Erreur de génération de projet PRJ0033

La propriété 'Dépendances supplémentaires' pour la génération personnalisée étape pour le fichier 'fichier' contenait 'macro' dont l’évaluation donne 'expansion_macro'.

Une étape de génération personnalisée sur un fichier contenait une erreur dans ses dépendances supplémentaires, probablement en raison d’un problème d’évaluation de macros. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.

Pour résoudre cette erreur, corrigez la macro ou corriger la spécification de chemin d’accès. Le chemin d’accès évaluée est un chemin d’accès absolu du répertoire du projet.