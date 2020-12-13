---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1201'
title: Erreur des outils Éditeur de liens LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 2817e8f84d0a5d28aa012de5459eb7e09f383172
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341631"
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
