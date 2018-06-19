---
title: -PDBPATH | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 274c4a3742d99b1e4702ed332206b78dacebccbd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373666"
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *filename*  
 Le nom du fichier .dll ou .exe pour lequel vous souhaitez trouver le fichier .pdb correspondant.  
  
 COMMENTAIRES (facultatif)  
 Signale tous les répertoires où une tentative a été effectuée pour localiser le fichier .pdb.  
  
## <a name="remarks"></a>Notes  
 /PDBPATH l’ordinateur en suivant les mêmes chemins que le débogueur pour recherche un fichier .pdb et signalera qui, le cas échéant, les fichiers .pdb correspondant dans le fichier spécifié dans *nom de fichier*.  
  
 Lorsque vous utilisez le débogueur Visual Studio, vous pouvez rencontrer un problème dû au fait que le débogueur utilise un fichier .pdb pour une autre version du fichier que vous déboguez.  
  
 /PDBPATH les fichiers .pdb avec les chemins d’accès suivants :  
  
-   Vérifiez l’emplacement où se trouve le fichier exécutable.  
  
-   Vérifiez l’emplacement du PDB écrit dans le fichier exécutable. Il s’agit généralement l’emplacement au moment où que l’image a été liée.  
  
-   Vérifiez le long du chemin de recherche configuré dans l’IDE de Visual Studio.  
  
-   Vérifiez les chemins dans _NT_SYMBOL_PATH et _NT_ALT_SYMBOL_PATH variables d’environnement.  
  
-   Vérifiez dans le répertoire Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Options DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/PDBALTPATH (Utiliser un autre chemin PDB)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)