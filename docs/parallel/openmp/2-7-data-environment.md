---
title: 2.7 environnement des données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690063"
---
# <a name="27-data-environment"></a>2.7 Environnement des données
Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution de régions parallèles, comme suit :  
  
-   A **threadprivate** directive (voir la section suivante) est fournie pour portée de fichier, espace de noms de portée ou variables static de portée de bloc local à un thread.  
  
-   Les clauses qui peuvent être spécifiées sur les directives pour contrôler les attributs de partage des variables pour la durée des constructions parallèles ou partage de travail sont décrites dans [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.