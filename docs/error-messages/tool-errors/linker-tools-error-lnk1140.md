---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1140'
title: Erreur des outils Éditeur de liens LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: cde57e3594035aecc1cc3608d1329c5bc0752624
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281195"
---
# <a name="linker-tools-error-lnk1140"></a>Erreur des outils Éditeur de liens LNK1140

trop de modules pour la base de données du programme ; lien avec/PDB : NONE

Le projet contient plus de 4096 modules.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Recréer un lien à l’aide de l' [option/pdb : None](../../build/reference/pdb-use-program-database.md).

1. Compilez des modules sans informations de débogage.

1. Réduisez le nombre de modules.
