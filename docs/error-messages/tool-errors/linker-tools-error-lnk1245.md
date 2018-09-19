---
title: Erreur des LNK1245 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041790"
---
# <a name="linker-tools-error-lnk1245"></a>Erreur des outils Éditeur de liens LNK1245

sous-système non valide « sous-système » spécifié ; /SUBSYSTEM doit être WINDOWS, WINDOWSCE ou CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) a été utilisé pour compiler l’objet et une des conditions suivantes a été rencontrée :

- Un point d’entrée personnalisé a été défini ([/Entry](../../build/reference/entry-entry-point-symbol.md)), de sorte que l’éditeur de liens n’a pas pu déduire un sous-système.

- La valeur passée à la [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option de l’éditeur de liens qui n’est pas valide pour les objets / CLR.

Dans les deux cas, la résolution est de spécifier une valeur valide pour l’option de l’éditeur de liens /SUBSYSTEM.