---
title: -ALLOWBIND (éviter la liaison DLL) | Microsoft Docs
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
ms.openlocfilehash: a0bff9ec6502aab5787c492a15e008bc29926163
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42571700"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Éviter la liaison DLL)
```  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 /ALLOWBIND:NO définit un bit dans l'en-tête d'une DLL, qui indique à Bind.exe que l'image n'est pas autorisée à être liée. Vous ne voulez peut-être pas qu’une DLL soit liée si elle a été signée numériquement (la liaison invalide la signature).  
  
 Vous pouvez modifier une DLL existante pour la fonctionnalité /ALLOWBIND à le [/ALLOWBIND](../../build/reference/allowbind.md) option de l’utilitaire EDITBIN.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez **propriétés de Configuration**, **l’éditeur de liens**, puis sélectionnez **ligne de commande**.  
  
3.  Entrez `/ALLOWBIND:NO` dans **des Options supplémentaires**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [BindImage (fonction)](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)   
 [BindImageEx (fonction)](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)