---
title: 2.7 Environnement des données
ms.date: 11/04/2016
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
ms.openlocfilehash: b65dfc7d7694b36ef4f89351579cd73e07ab537c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491964"
---
# <a name="27-data-environment"></a>2.7 Environnement des données

Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution des régions parallèles, comme suit :

- Un **threadprivate** directive (voir la section suivante) est fournie pour portée de fichier, portée de l’espace de noms ou les variables statiques de portée de bloc local à un thread.

- Les clauses qui peuvent être spécifiées sur les directives pour contrôler les attributs de partage de variables pour la durée des constructions parallèles ou partage de travail sont décrits dans [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.