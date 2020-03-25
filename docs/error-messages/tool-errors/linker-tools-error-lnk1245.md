---
title: Erreur des outils Éditeur de liens LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183798"
---
# <a name="linker-tools-error-lnk1245"></a>Erreur des outils Éditeur de liens LNK1245

sous-système « Subsystem » non valide spécifié ; /SUBSYSTEM doit être WINDOWS, WINDOWSCE ou CONSOLE

[/CLR](../../build/reference/clr-common-language-runtime-compilation.md) a été utilisé pour compiler l’objet et l’une des conditions suivantes était vraie :

- Un point d’entrée personnalisé a été défini ([/entry](../../build/reference/entry-entry-point-symbol.md)), de sorte que l’éditeur de liens n’a pas pu déduire un sous-système.

- Une valeur a été passée à l’option [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) de l’éditeur de liens qui n’est pas valide pour les objets/CLR.

Dans les deux cas, la solution consiste à spécifier une valeur valide pour l’option de l’éditeur de liens/SUBSYSTEM.
