---
title: 'Gestion de la mémoire : Allocation des tas | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99df4a50f021e0981354a5d316606729bb824d94
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352410"
---
# <a name="memory-management-heap-allocation"></a>Gestion de la mémoire : allocation de tas
Le segment de mémoire est réservée pour les besoins de l’allocation de mémoire du programme. Il s’agit d’une zone en dehors du code du programme et de la pile. Les programmes C utilisent les fonctions `malloc` et **libre** pour allouer et libérer la mémoire du segment. La version Debug des MFC fournit des versions modifiées des opérateurs intégrés C++ **nouveau** et **supprimer** pour allouer et libérer des objets dans la mémoire du segment de mémoire.  
  
 Lorsque vous utilisez **nouveau** et **supprimer** au lieu de `malloc` et **libre**, vous êtes en mesure de tirer parti des améliorations de débogage de gestion de la mémoire de la bibliothèque de classes , qui peut être utile dans la détection des fuites de mémoire. Lorsque vous générez votre programme avec la version Release de MFC, les versions standards de la **nouveau** et **supprimer** opérateurs offrent un moyen efficace pour allouer et libérer la mémoire (la version de MFC ne fournit pas des versions modifiées de ces opérateurs).  
  
 Notez que la taille totale des objets alloués sur le tas est limitée uniquement par la mémoire virtuelle de votre système.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire](../mfc/memory-management.md)

