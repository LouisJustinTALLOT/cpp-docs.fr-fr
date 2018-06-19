---
title: Erreur LNK1277 des outils Éditeur de liens | Documents Microsoft
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
ms.openlocfilehash: ec8f00793fcda748c60d9d8ea775611e3d025cd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298728"
---
# <a name="linker-tools-error-lnk1277"></a>Erreur des outils Éditeur de liens LNK1277
enregistrement objet introuvable dans pgd (NomFichier)  
  
 Lorsque vous utilisez [/LTCG : PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), le chemin d’accès de l’un des fichiers d’entrée .lib, def ou .obj était différent du chemin d’accès sur lequel ils ont été trouvés lors de/LTCG : PGINSTRUMENT. Cela peut s’expliquer par une modification de la variable d’environnement LIB après/LTCG : PGINSTRUMENT. Le chemin d’accès complet aux fichiers d’entrée est stockée dans le fichier .pgd.  
  
 / LTCG : PGOPTIMIZE requiert que les entrées soient identiques à la phase de/LTCG : PGINSTRUMENT.  
  
 Pour résoudre cet avertissement, effectuez l’une des opérations suivantes :  
  
-   Exécutez/LTCG : PGINSTRUMENT, restauration par progression de toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE.  
  
-   Modifier la variable d’environnement LIB pour qu’il avait lors de l’exécution / LTCG : PGINSTRUMENT.  
  
 Il est déconseillé de contourner LNK1277 à l’aide de/LTCG : PGUPDATE.