---
title: Erreur irrécupérable RW1025 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba216e63cb0cae92b4541800493a2fb6195553a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320012"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Erreur irrécupérable RW1025 du compilateur de ressources 
La mémoire de tas lointain  
  
 Rechercher les logiciels de résidant en mémoire qui peut occuper trop d’espace. Le programme CHKDSK permet de déterminer la quantité de mémoire.  
  
 Si vous créez un fichier de ressources volumineux, fractionner le script de ressources en deux fichiers. Après avoir créé les deux fichiers .res, utilisez la ligne de commande MS-DOS pour joindre les :  
  
```  
copy first.res /b + second.res /b full.res  
```