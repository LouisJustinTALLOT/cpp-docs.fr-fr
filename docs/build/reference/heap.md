---
title: -TAS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /heap
dev_langs:
- C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5306df647801d7d1467aa0f44bfacca18fccaff3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372215"
---
# <a name="heap"></a>/HEAP
Définit la taille du segment de mémoire en octets. Cette option s’applique uniquement aux fichiers exécutables.  
  
```  
  
/HEAP:  
reserve[,commit]  
```  
  
## <a name="remarks"></a>Notes  
 Le `reserve` argument spécifie l’allocation initiale totale des tas dans la mémoire virtuelle. Par défaut, la taille du tas est de 1 Mo. [Référence EDITBIN](../../build/reference/editbin-reference.md) arrondit la valeur spécifiée au multiple plus proche de 4 octets.  
  
 Le paramètre facultatif `commit` argument est soumis à l’interprétation par le système d’exploitation. Sur un système d’exploitation Windows, il spécifie la quantité initiale de mémoire physique à allouer et de la quantité de mémoire supplémentaire pour allouer le segment de mémoire doit être développé. Mémoire virtuelle dédiée, espace à réserver dans le fichier d’échange. Un degré plus élevé `commit` valeur permet au système allouer de la mémoire moins souvent lors de l’application a besoin de davantage d’espace du tas, mais augmente les besoins en mémoire et peut allonger la durée de démarrage d’application. Le `commit` valeur doit être inférieure ou égale à la `reserve` valeur.  
  
 Spécifiez le `reserve` et `commit` les valeurs dans la notation décimale ou en langage C hexadécimale ou octale. Par exemple, une valeur de 1 Mo peut être spécifiée en tant que 1048576 au format décimal, ou 0 x 100000 en hexadécimal ou 04000000 dans octal.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)