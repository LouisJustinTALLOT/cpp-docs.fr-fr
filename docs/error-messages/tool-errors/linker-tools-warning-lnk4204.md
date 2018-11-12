---
title: Avertissement des outils Éditeur de liens LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475162"
---
# <a name="linker-tools-warning-lnk4204"></a>Avertissement des outils Éditeur de liens LNK4204

'nom_fichier' manque d’informations de débogage pour référencer le module ; objet sera lié sans informations de débogage

Le fichier .pdb a une signature erronée. L’éditeur de liens poursuit la liaison de l’objet sans informations de débogage. Vous souhaiterez peut-être recompiler le fichier objet en utilisant le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option.

LNK4204 peut se produire si certains des objets dans la bibliothèque font référence à un fichier qui n’existe plus. Cela peut arriver lors de la régénération de la solution, par exemple ; un fichier objet peut être supprimé et pas reconstruit en raison d’une erreur de compilation. Dans ce cas, compilez avec **/Z7**, ou **/Fd**, pour mettre à jour les objets pour faire référence à un fichier unique par bibliothèque (qui n’est pas le nom de fichier .pdb par défaut).  Pour plus d’informations, consultez l’article [/Fd (Nom de fichier PDB)](../../build/reference/fd-program-database-file-name.md).  Vérifiez que le fichier .pdb est enregistré avec la bibliothèque chaque fois qu’il est mis à jour dans le système de contrôle source.