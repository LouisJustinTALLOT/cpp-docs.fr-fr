---
title: Erreur BSCMAKE BK1509 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825d1e1e119aa80445c5ae15804bbdde4a3d8bf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295621"
---
# <a name="bscmake-error-bk1509"></a>Erreur BSCMAKE BK1509
espace du tas insuffisant  
  
 BSCMAKE n’a plus de mémoire, y compris la mémoire virtuelle.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Libérez de l’espace disque.  
  
2.  Augmentez la taille du fichier d’échange.  
  
3.  Augmentez la taille du fichier d’échange Windows.  
  
4.  Réduire la mémoire avec BSCMAKE, à l’aide de /Ei ou /Es à supprimer certains fichiers d’entrée ou /Em pour éliminer les corps de la macro.