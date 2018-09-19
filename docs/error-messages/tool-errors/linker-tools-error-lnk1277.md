---
title: Erreur LNK1277 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082515"
---
# <a name="linker-tools-error-lnk1277"></a>Erreur des outils Éditeur de liens LNK1277

enregistrement objet introuvable dans pgd (NomFichier)

Lorsque vous utilisez [/LTCG : PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), le chemin d’accès d’un des fichiers d’entrée .lib, def ou .obj était différent du chemin d’accès sur lequel ils ont été trouvés lors/LTCG : PGINSTRUMENT. Cela peut s’expliquer par une modification dans la variable d’environnement LIB après/LTCG : PGINSTRUMENT. Le chemin d’accès complet aux fichiers d’entrée est stockée dans le fichier .pgd.

/ LTCG : PGOPTIMIZE exige que les entrées soit identique à la phase / LTCG : PGINSTRUMENT.

Pour résoudre cet avertissement, effectuez l’une des opérations suivantes :

- Exécutez/LTCG : PGINSTRUMENT, restauration par progression de toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE.

- Modifier la variable d’environnement LIB pour qu’il avait lors de l’exécution / LTCG : PGINSTRUMENT.

Il est déconseillé de contourner LNK1277 à l’aide de/LTCG : PGUPDATE.