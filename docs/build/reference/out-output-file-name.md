---
title: -OUT (nom de fichier de sortie) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
dev_langs:
- C++
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fd9ec1b1631104355e076071370f627a36b4037
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376103"
---
# <a name="out-output-file-name"></a>/OUT (Nom du fichier de sortie)
```  
/OUT:filename  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *filename*  
 Nom du fichier de sortie spécifié par l’utilisateur. Il remplace le nom par défaut.  
  
## <a name="remarks"></a>Notes  
 L’option /OUT substitue le nom par défaut et l’emplacement du programme qui crée de l’éditeur de liens.  
  
 Par défaut, l’éditeur de liens constitue le nom de fichier à l’aide du nom de base du premier fichier .obj spécifié et l’extension appropriée (.exe ou .dll).  
  
 Cette option le nom de base par défaut pour une bibliothèque de fichier de mappage ou d’importation. Pour plus d’informations, consultez [générer fichier de mappage](../../build/reference/map-generate-mapfile.md) (/Map) et [/IMPLIB](../../build/reference/implib-name-import-library.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **général** page de propriétés.  
  
4.  Modifier la **fichier de sortie** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)