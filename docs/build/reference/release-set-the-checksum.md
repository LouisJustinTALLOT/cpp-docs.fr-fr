---
title: -RELEASE (jeu de la somme de contrôle) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
dev_langs:
- C++
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d360ad7264cb66da140df340bc9d281a329c26c2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375150"
---
# <a name="release-set-the-checksum"></a>/RELEASE (Définir le total de Checksum)
```  
/RELEASE  
```  
  
## <a name="remarks"></a>Notes  
 L’option /RELEASE définit le Checksum dans l’en-tête d’un fichier .exe.  
  
 Le système d’exploitation requiert la somme de contrôle pour les pilotes de périphérique. Définissez la somme de contrôle pour les versions des pilotes de périphérique pour assurer la compatibilité avec les futurs systèmes d’exploitation.  
  
 L’option /RELEASE est définie par défaut lors de la [/SUBSYSTEM : native](../../build/reference/subsystem-specify-subsystem.md) option est spécifiée.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **activation du Checksum** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)