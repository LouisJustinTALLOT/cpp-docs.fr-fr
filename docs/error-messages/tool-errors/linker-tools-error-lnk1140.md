---
title: Erreur des LNK1140 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f850360bc749a41e548cebae9f58f9fc7d3d420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044702"
---
# <a name="linker-tools-error-lnk1140"></a>Erreur des outils Éditeur de liens LNK1140

trop de modules pour la base de données du programme ; Liez avec/PDB : NONE

Le projet contient des modules de plus de 4 096.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Relier à l’aide de [/PDB : NONE](../../build/reference/pdb-use-program-database.md).

1. Compilez certains modules sans informations de débogage.

1. Réduire le nombre de modules.