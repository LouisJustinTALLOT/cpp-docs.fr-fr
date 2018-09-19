---
title: Erreur des LNK1201 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c133748f95846160e1387e31e023d9ce459b281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055259"
---
# <a name="linker-tools-error-lnk1201"></a>Erreur des outils Éditeur de liens LNK1201

Erreur d’écriture dans la base de données de programme 'nom_fichier' ; Recherchez un espace disque insuffisant, chemin d’accès non valide ou privilège insuffisant

LIEN n’a pas pu écrire dans la base de données de programme (PDB) pour le fichier de sortie.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Fichier est endommagé. Supprimer le fichier PDB et les relier.

1. Espace disque insuffisant pour écrire le fichier.

1. Lecteur n’est pas disponible, probablement en raison d’un problème réseau.

1. Le débogueur est actif sur le programme que vous voulez lier.

1. Espace du tas insuffisant.  Consultez [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) pour plus d’informations.