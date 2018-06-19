---
title: Erreur BSCMAKE BK1506 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e19ec77818c8017387519b03e400c09d47021bc5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300421"
---
# <a name="bscmake-error-bk1506"></a>Erreur BSCMAKE BK1506
Impossible d’ouvrir le fichier 'nom_fichier' [ : raison]  
  
 BSCMAKE ne peut pas ouvrir le fichier.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Fichier est verrouillé par un autre processus. Si `reason` indique que **autorisation refusée**, le navigateur peut être à l’aide du fichier. Fermez la fenêtre de navigation et recommencez la génération.  
  
2.  Un disque saturé.  
  
3.  Une erreur matérielle.  
  
4.  Le fichier de sortie spécifié a le même nom qu’un sous-répertoire existant.