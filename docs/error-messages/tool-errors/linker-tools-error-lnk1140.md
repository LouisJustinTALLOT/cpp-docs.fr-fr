---
title: Erreur des outils Éditeur de liens LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482463"
---
# <a name="linker-tools-error-lnk1140"></a>Erreur des outils Éditeur de liens LNK1140

trop de modules pour la base de données du programme ; Liez avec/PDB : NONE

Le projet contient des modules de plus de 4 096.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Relier à l’aide de [/PDB : NONE](../../build/reference/pdb-use-program-database.md).

1. Compilez certains modules sans informations de débogage.

1. Réduire le nombre de modules.