---
title: Erreur des outils Éditeur de liens LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386523"
---
# <a name="linker-tools-error-lnk2008"></a>Erreur des outils Éditeur de liens LNK2008

Cible de correction n’est pas alignée 'nom_symbole'

LINK a trouvé une cible de correction dans votre fichier objet qui n’était pas correctement aligné.

Cette erreur peut être provoquée par personnalisé d’un alignement de (par exemple, #pragma [pack](../../preprocessor/pack.md)), [aligner](../../cpp/align-cpp.md) modificateur, ou à l’aide de code en langage assembleur qui modifie l’alignement.

Si votre code n’utilise aucun des éléments ci-dessus, cela peut être dû par le compilateur.