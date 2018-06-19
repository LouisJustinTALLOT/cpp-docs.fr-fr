---
title: -LINENUMBERS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /linenumbers
dev_langs:
- C++
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9202d7f46dbd3a619e379d076db217544bd4291
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371757"
---
# <a name="linenumbers"></a>/LINENUMBERS
```  
/LINENUMBERS  
```  
  
## <a name="remarks"></a>Notes  
 Cette option affiche les numéros de ligne COFF. Les numéros de ligne existent dans un fichier objet si elle a été compilée avec le programme de base de données (/ Zi), Compatible C7 (/ Z7), ou les numéros de ligne uniquement (/Zd). Un fichier exécutable ou DLL contient les numéros de ligne COFF si elle a été lié à générer des infos de débogage (/Debug).  
  
 Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés par le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.  
  
## <a name="see-also"></a>Voir aussi  
 [DUMPBIN, options](../../build/reference/dumpbin-options.md)