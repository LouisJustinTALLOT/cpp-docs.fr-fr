---
title: Erreur des outils Éditeur de liens LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195264"
---
# <a name="linker-tools-error-lnk1140"></a>Erreur des outils Éditeur de liens LNK1140

trop de modules pour la base de données du programme ; lien avec/PDB : NONE

Le projet contient plus de 4096 modules.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Recréer un lien à l’aide de l' [option/pdb : None](../../build/reference/pdb-use-program-database.md).

1. Compilez des modules sans informations de débogage.

1. Réduisez le nombre de modules.
