---
title: Erreur des outils Éditeur de liens LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195108"
---
# <a name="linker-tools-error-lnk1201"></a>Erreur des outils Éditeur de liens LNK1201

erreur lors de l’écriture dans la base de données du programme’nom_fichier'; Vérifiez que l’espace disque est insuffisant, le chemin d’accès n’est pas valide ou le privilège est insuffisant

Le lien n’a pas pu écrire dans la base de données du programme (PDB) pour le fichier de sortie.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le fichier est endommagé. Supprimez le fichier PDB et reliez-le.

1. Espace disque insuffisant pour l’écriture du fichier.

1. Le lecteur n’est pas disponible, peut-être en raison d’un problème réseau.

1. Le débogueur est actif sur le programme que vous essayez de lier.

1. Espace du tas insuffisant.  Pour plus d’informations, consultez [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
