---
title: -FORCE (Force du fichier de sortie) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1daa27ce48590d4a122eafde9f63f7142271610
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373698"
---
# <a name="force-force-file-output"></a>/FORCE (Forcer la sortie d'un fichier)
```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## <a name="remarks"></a>Notes  
 L’option /FORCE indique à l’éditeur de liens pour créer un fichier .exe valide ou DLL même si un symbole est référencé mais pas défini ou est défini plusieurs fois.  
  
 L’option peut prendre un argument facultatif :  
  
-   Multiple permet de créer un fichier de sortie si LINK trouve plusieurs définitions pour un symbole ou non.  
  
-   Option/force : UNRESOLVED crée un fichier de sortie si LINK trouve un symbole non défini ou non. / FORCE : non RÉSOLUE est ignorée si le symbole de point d’entrée n’est pas résolu.  
  
 /FORCE sans argument implique les deux multiples et non résolus.  
  
 Un fichier créé avec cette option peut ne pas fonctionner comme prévu. L’éditeur de liens n’est pas lier par incrément lorsque l’option /FORCE est spécifiée.  
  
 Si un module est compilé avec **/CLR**, **/force** ne crée pas d’image.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l’option dans le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)