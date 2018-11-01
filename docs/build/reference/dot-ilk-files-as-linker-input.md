---
title: Fichiers .ilk en tant qu'entrée dans l'éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 012ca9aaa50ac2f8bb9d95ef77df5bb7127c5b79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595973"
---
# <a name="ilk-files-as-linker-input"></a>Fichiers .ilk en tant qu'entrée dans l'éditeur de liens

Lors de la liaison incrémentielle, lien met à jour le fichier d’état .ilk créé pendant le premier lien incrémentiel. Ce fichier a le même nom de base que le fichier .exe ou .dll, et il porte l’extension .ilk. Au cours des liens incrémentiels à venir, lien met à jour le fichier .ilk. Si le fichier .ilk est manquant, LINK effectue un lien complet et crée un nouveau fichier .ilk. Si le fichier .ilk est inutilisable, LINK effectue un lien non incrémentielle. Pour plus d’informations sur la liaison incrémentielle, consultez le [lier par incrément (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) option.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)