---
title: 'Gestion de la mémoire : Allocation de tas | Microsoft Docs'
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
ms.openlocfilehash: cc158ceda21bfb04053bbc490a3333a76e2d7afe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383809"
---
# <a name="memory-management-heap-allocation"></a>Gestion de la mémoire : allocation de tas

Le segment de mémoire est réservée pour les besoins de l’allocation de mémoire du programme. Il est une zone en dehors du code de programme et de la pile. Les programmes C utilisent les fonctions **malloc** et **gratuit** pour allouer et libérer la mémoire de tas. La version Debug des MFC fournit des versions modifiées des opérateurs intégrés C++ **nouveau** et **supprimer** pour allouer et libérer des objets dans la mémoire de tas.

Lorsque vous utilisez **nouveau** et **supprimer** au lieu de **malloc** et **gratuit**, vous êtes en mesure de tirer parti de la bibliothèque de classes améliorations débogage de gestion de la mémoire, qui peuvent être utiles pour détecter les fuites de mémoire. Lorsque vous générez votre programme avec la version Release de MFC, les versions standards de la **nouveau** et **supprimer** opérateurs offrent un moyen efficace pour allouer et libérer la mémoire (la version de MFC ne fournit pas des versions modifiées de ces opérateurs).

Notez que la taille totale des objets alloués sur le tas est limitée uniquement par la mémoire virtuelle de votre système.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire](../mfc/memory-management.md)

