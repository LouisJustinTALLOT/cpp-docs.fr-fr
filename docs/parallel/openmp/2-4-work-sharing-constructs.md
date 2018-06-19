---
title: 2.4 constructions de partage de travail | Documents Microsoft
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
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689634"
---
# <a name="24-work-sharing-constructs"></a>2.4 Constructions de partage de travail
Une construction de partage de travail répartit l’exécution de l’instruction associée parmi les membres de l’équipe que vous rencontrez. Les directives de partage de travail ne pas lancent de nouveaux threads, et il n’existe aucune barrière implicite sur ENTRÉE pour une construction de partage de travail.  
  
 La séquence de partage de travail construit et **barrière** directives rencontrés doivent être identiques pour chaque thread dans une équipe.  
  
 OpenMP définit les constructions de partage de travail suivantes, et que ceux-ci sont décrits dans les sections qui suivent :  
  
-   **pour** (directive)  
  
-   **sections** (directive)  
  
-   **seul** (directive)