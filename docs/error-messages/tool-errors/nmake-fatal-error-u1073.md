---
title: Erreur irrécupérable NMAKE U1073 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dde9ca2f4a15edf6599dcc31b39d9411645f2a6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316304"
---
# <a name="nmake-fatal-error-u1073"></a>Erreur irrécupérable NMAKE U1073
incapable de rendre 'targetname'  
  
 La cible spécifiée n’existe pas, et aucune commande à exécuter ou d’une règle d’inférence à appliquer.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Vérifiez l’orthographe du nom de la cible.  
  
2.  Si *targetname* est une pseudocible, spécifiez-la en tant que cible dans un autre bloc de description.  
  
3.  Si *targetname* est un appel de macro, veillez à ne développe pas une chaîne null.