---
title: -SWAPRUN | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /swaprun
dev_langs:
- C++
helpviewer_keywords:
- /SWAPRUN editbin option
- -SWAPRUN editbin option
- SWAPRUN editbin option
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e8af5b23d2e6cd0759f75c4054e0a811f687e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375046"
---
# <a name="swaprun"></a>/SWAPRUN
```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## <a name="remarks"></a>Notes  
 Cette option modifie l’image pour indiquer au système d’exploitation pour copier l’image dans un fichier d’échange et exécutez-le à partir de là. Utilisez cette option pour les images qui résident sur des réseaux ou un support amovible.  
  
 Vous pouvez ajouter ou supprimer les qualificateurs NET ou CD :  
  
-   NET indique que l’image réside sur un réseau.  
  
-   CD indique que l’image se trouve sur un CD-ROM ou un support amovible similaire.  
  
-   Utilisez ! NET et ! CD pour inverser les effets de NET et CD.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)