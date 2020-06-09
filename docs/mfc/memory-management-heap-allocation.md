---
title: 'Gestion de la mémoire : allocation de tas'
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626281"
---
# <a name="memory-management-heap-allocation"></a>Gestion de la mémoire : allocation de tas

Le tas est réservé aux besoins d’allocation de mémoire du programme. Il s’agit d’une zone séparée du code du programme et de la pile. Les programmes C typiques utilisent les fonctions **malloc** et Free pour allouer et **libérer** de la mémoire du tas. La version de débogage de MFC fournit des versions modifiées des opérateurs intégrés C++ **New** et **Delete** pour allouer et libérer des objets dans la mémoire du tas.

Lorsque vous utilisez **New** et **Delete** au lieu de **malloc** et **Free**, vous pouvez tirer parti des améliorations du débogage de la gestion de la mémoire de la bibliothèque de classes, ce qui peut être utile pour détecter les fuites de mémoire. Quand vous générez votre programme avec la version finale de MFC, les versions standard des opérateurs **New** et **Delete** offrent un moyen efficace d’allouer et de libérer de la mémoire (la version Release de MFC ne fournit pas de versions modifiées de ces opérateurs).

Notez que la taille totale des objets alloués sur le tas est limitée uniquement par la mémoire virtuelle disponible de votre système.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire](memory-management.md)
