---
title: -EXPORT (exporter une fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366b40e8e40e62f67ec45f3e59ad61eb338c427
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374490"
---
# <a name="export-exports-a-function"></a>/EXPORT (Exporter une fonction)
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>Notes  
 Avec cette option, vous pouvez exporter une fonction à partir de votre programme afin que d’autres programmes peuvent appeler la fonction. Vous pouvez également exporter des données. Les exportations sont généralement définies dans une DLL.  
  
 Le *nom d’entrée* est le nom de l’élément de données ou de la fonction tel qu’il doit être utilisé par le programme appelant. `ordinal` Spécifie un index dans la table d’exportations compris entre 1 et 65 535 ; Si vous ne spécifiez pas `ordinal`, assigne un. Le **NONAME** mot clé exporte la fonction uniquement comme ordinal, sans une *nom d’entrée*.  
  
 Le **données** mot clé indique que l’élément exporté est un élément de données. L’élément de données dans le programme client doit être déclaré à l’aide de **extern __declspec (dllimport)**.  
  
 Il existe trois méthodes pour l’exportation d’une définition, répertoriées dans l’ordre d’utilisation recommandé :  
  
1.  [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source  
  
2.  Un [exportations](../../build/reference/exports.md) instruction dans un fichier .def  
  
3.  Une spécification /EXPORT dans une commande LINK  
  
 Les trois méthodes peuvent être utilisés dans le même programme. Quand LINK génère un programme contenant des exportations, il crée également une bibliothèque d’importation, sauf si un fichier .exp est utilisé dans la build.  
  
 LINK utilise les formes décorées des identificateurs. Le compilateur décore un identificateur lorsqu’il crée le fichier .obj. Si *nom d’entrée* est spécifiée pour l’éditeur de liens dans son non décoré écran (tel qu’il apparaît dans le code source), LINK tente de correspondre au nom. Si elle ne peut pas trouver une correspondance unique, LINK émet un message d’erreur. Utilisez le [DUMPBIN](../../build/reference/dumpbin-reference.md) outil pour obtenir le [noms décorés](../../build/reference/decorated-names.md) forme d’un identificateur lorsque vous devez spécifier à l’éditeur de liens.  
  
> [!NOTE]
>  Ne spécifiez pas la forme décorée d’identificateurs en langage C qui sont déclarés `__cdecl` ou `__stdcall`.  
  
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