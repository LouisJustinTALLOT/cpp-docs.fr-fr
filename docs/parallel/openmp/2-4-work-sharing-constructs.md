---
title: 2.4 constructions de partage de travail | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411116"
---
# <a name="24-work-sharing-constructs"></a>2.4 Constructions de partage de travail

Une construction de partage de travail répartit l’exécution de l’instruction associée parmi les membres de l’équipe qui la rencontrer. Les directives de partage de travail ne pas lancent de nouveaux threads, et il n’existe plus aucune barrière implicite sur ENTRÉE pour une construction de partage de travail.

La séquence de partage de travail construit et **barrière** directives rencontrés doivent être le même pour chaque thread dans une équipe.

OpenMP définit les constructions de partage de travail suivantes, et ceux-ci sont décrits dans les sections qui suivent :

- **pour** (directive)

- **sections** (directive)

- **seul** (directive)