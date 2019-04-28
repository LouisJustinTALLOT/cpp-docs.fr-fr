---
title: Conventions d'appel obsolètes
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245020"
---
# <a name="obsolete-calling-conventions"></a>Conventions d'appel obsolètes

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Le **__pascal**, **__fortran**, et **__syscall** conventions d’appel ne sont plus prises en charge. Vous pouvez émuler leurs fonctionnalités en utilisant l’une des conventions d’appel prises en charge et les options appropriées de l’Éditeur de liens.

\<Windows.h > prend désormais en charge la macro WINAPI, qui se traduit par la convention d’appel appropriée pour la cible. Utilisez WINAPI où vous avez utilisé précédemment PASCAL ou **__far \__pascal**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)