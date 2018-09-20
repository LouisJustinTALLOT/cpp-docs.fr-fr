---
title: 2.5 constructions de partage de travail parallèles combinées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 45936e5a-c62a-4eea-a8f4-232210c9d0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c456eceb39d969e6841e3d3bf9028fae4bf5000
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404759"
---
# <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 Constructions de partage de travail parallèle combinées

Constructions de partage de travail parallèles combinées sont des raccourcis permettant de spécifier une région parallèle qui contient uniquement une construction de partage de travail. La sémantique de ces directives est identique à celle de spécifier explicitement un **parallèles** directive suivie d’une construction de partage de travail unique.

Les sections suivantes décrivent les constructions de partage de travail parallèles combinées :

- le **parallèles pour** la directive.

- le **de sections parallèles** directive.