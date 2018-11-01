---
title: Avertissement des outils Éditeur de liens LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 1c9ccfe6ca201ae4deed69c7d01429c67cce4bda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552475"
---
# <a name="linker-tools-warning-lnk4022"></a>Avertissement des outils Éditeur de liens LNK4022

Impossible de trouver une correspondance unique pour le symbole 'symbole'

LIEN ou LIB a trouvé plusieurs correspondances pour le symbole non décoré donné et ne peut pas résoudre l’ambiguïté. Aucun fichier de sortie (.exe, .dll, .exp ou .lib) n’est généré. Cet avertissement est suivi par un avertissement [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pour chaque dupliquer le symbole et finalement suivi de l’erreur irrécupérable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Pour éviter cet avertissement, spécifiez le symbole dans sa forme décorée. Exécutez [DUMPBIN](../../build/reference/dumpbin-options.md) sur l’objet pour voir les noms décorés.