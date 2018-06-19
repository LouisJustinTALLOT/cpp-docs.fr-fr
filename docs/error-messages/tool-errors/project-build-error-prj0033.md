---
title: PRJ0033 d’erreur de Build de projet | Documents Microsoft
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
ms.openlocfilehash: 2722bc53fe267d3327f265578435cb672c58d3f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317058"
---
# <a name="project-build-error-prj0033"></a>Erreur de génération de projet PRJ0033
La propriété 'Dépendances supplémentaires' pour la génération personnalisée étape pour le fichier 'fichier' contenait 'macro', dont l’évaluation donne 'expansion_macro'.  
  
 Une étape de génération personnalisée sur un fichier contenait une erreur dans ses dépendances supplémentaires, probablement en raison d’un problème d’évaluation de macro. Cette erreur peut aussi signifier que le chemin d’accès est incorrect, contenant des caractères ou des combinaisons de caractères qui ne sont pas autorisés dans un chemin d’accès de fichier.  
  
 Pour résoudre cette erreur, corrigez la macro ou corrigez la spécification de chemin d’accès. Le chemin d’accès évalué est un chemin d’accès absolu du répertoire de projet.