---
title: 2.7 environnement des données | Microsoft Docs
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
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378135"
---
# <a name="27-data-environment"></a>2.7 Environnement des données

Cette section présente une directive et plusieurs clauses pour contrôler l’environnement de données pendant l’exécution des régions parallèles, comme suit :

- Un **threadprivate** directive (voir la section suivante) est fournie pour portée de fichier, portée de l’espace de noms ou les variables statiques de portée de bloc local à un thread.

- Les clauses qui peuvent être spécifiées sur les directives pour contrôler les attributs de partage de variables pour la durée des constructions parallèles ou partage de travail sont décrits dans [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.