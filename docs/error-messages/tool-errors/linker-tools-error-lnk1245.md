---
title: Erreur des outils Éditeur de liens LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160560"
---
# <a name="linker-tools-error-lnk1245"></a>Erreur des outils Éditeur de liens LNK1245

sous-système non valide « sous-système » spécifié ; /SUBSYSTEM doit être WINDOWS, WINDOWSCE ou CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) a été utilisé pour compiler l’objet et une des conditions suivantes a été rencontrée :

- Un point d’entrée personnalisé a été défini ([/Entry](../../build/reference/entry-entry-point-symbol.md)), de sorte que l’éditeur de liens n’a pas pu déduire un sous-système.

- La valeur passée à la [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option de l’éditeur de liens qui n’est pas valide pour les objets / CLR.

Dans les deux cas, la résolution est de spécifier une valeur valide pour l’option de l’éditeur de liens /SUBSYSTEM.