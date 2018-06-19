---
title: -WINMDFILE (spécifier un fichier) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eaf1bfc805db568a012c28d66361bbd99745a95
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375595"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (spécifier un fichier winmd)
Spécifie le nom de fichier pour le fichier de sortie de métadonnées Windows Runtime (.winmd) qui est généré par le [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) option de l’éditeur de liens.  
  
```  
/WINMDFILE:filename  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez la valeur spécifiée dans `filename` pour remplacer le nom de fichier .winmd (`binaryname`.winmd). Notez que vous n’ajoutez pas de « .winmd » au `filename`.  Si plusieurs valeurs sont répertoriés sur le **/WINMDFILE** ligne de commande, le dernier est prioritaire.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **l’éditeur de liens** dossier.  
  
3.  Sélectionnez le **métadonnées Windows** page de propriétés.  
  
4.  Dans le **fichier de métadonnées Windows** , entrez l’emplacement du fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [/WINMD (générer des métadonnées Windows)](../../build/reference/winmd-generate-windows-metadata.md)   
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)