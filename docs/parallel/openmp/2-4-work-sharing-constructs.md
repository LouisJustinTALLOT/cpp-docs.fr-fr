---
title: 2.4 Constructions de partage de travail
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502880"
---
# <a name="24-work-sharing-constructs"></a>2.4 Constructions de partage de travail

Une construction de partage de travail répartit l’exécution de l’instruction associée parmi les membres de l’équipe qui la rencontrer. Les directives de partage de travail ne pas lancent de nouveaux threads, et il n’existe plus aucune barrière implicite sur ENTRÉE pour une construction de partage de travail.

La séquence de partage de travail construit et **barrière** directives rencontrés doivent être le même pour chaque thread dans une équipe.

OpenMP définit les constructions de partage de travail suivantes, et ceux-ci sont décrits dans les sections qui suivent :

- **pour** (directive)

- **sections** (directive)

- **seul** (directive)