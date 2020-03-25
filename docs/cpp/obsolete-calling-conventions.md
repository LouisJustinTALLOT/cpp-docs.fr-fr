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
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188556"
---
# <a name="obsolete-calling-conventions"></a>Conventions d'appel obsolètes

**Section spécifique de Microsoft**

Les conventions d’appel **__pascal**, **__fortran**et **__syscall** ne sont plus prises en charge. Vous pouvez émuler leurs fonctionnalités en utilisant l’une des conventions d’appel prises en charge et les options appropriées de l’Éditeur de liens.

\<Windows. h > prend désormais en charge la macro WINAPI, qui se traduit par la Convention d’appel appropriée pour la cible. Utilisez WINAPI dans lequel vous avez précédemment utilisé PASCAL ou **__far \__pascal**.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)
