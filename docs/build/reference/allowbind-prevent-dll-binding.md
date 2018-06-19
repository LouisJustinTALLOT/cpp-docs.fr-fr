---
title: -/ALLOWBIND (éviter la liaison DLL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31968e27c46cb5ea220a4cfe19c36820c4cf8444
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369638"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Éviter la liaison DLL)
```  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 /ALLOWBIND:NO définit un bit dans l'en-tête d'une DLL, qui indique à Bind.exe que l'image n'est pas autorisée à être liée. Vous ne voulez peut-être pas qu’une DLL soit liée si elle a été signée numériquement (la liaison invalide la signature).  
  
 Vous pouvez modifier une DLL existante pour la fonctionnalité /ALLOWBIND avec la [/ALLOWBIND](../../build/reference/allowbind.md) option de l’utilitaire EDITBIN.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez **propriétés de Configuration**, **l’éditeur de liens**, puis sélectionnez **ligne de commande**.  
  
3.  Entrez `/ALLOWBIND:NO` dans **des Options supplémentaires**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [BindImage (fonction)](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [BindImageEx (fonction)](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)