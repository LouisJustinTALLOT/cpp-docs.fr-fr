---
title: Erreur de ligne de commande D8027 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296118"
---
# <a name="command-line-error-d8027"></a>Erreur de ligne de commande D8027
Impossible d’exécuter 'composant'  
  
 Le compilateur n’a pas pu exécuter le composant de donnée du compilateur ou l’éditeur de liens.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Mémoire insuffisante pour charger le composant. Si NMAKE a appelé le compilateur, exécutez le compilateur en dehors du makefile.  
  
2.  Le système d’exploitation actuel n’a pas pu exécuter le composant. Assurez-vous que le chemin pointe vers les fichiers exécutables correspondant à votre système d’exploitation.  
  
3.  Le composant a été endommagé. Recopiez le composant à partir de disques de distribution, à l’aide du programme d’installation.  
  
4.  Une option a été spécifiée correctement. Par exemple :  
  
    ```  
    cl /B1 file1.c  
    ```