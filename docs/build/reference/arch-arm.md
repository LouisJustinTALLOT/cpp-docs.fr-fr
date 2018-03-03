---
title: -arch (ARM) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 468401bcee2d627149175d022c420b8bb905c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="arch-arm"></a>/arch (ARM)
Spécifie l'architecture pour la génération de code sur ARM. Voir aussi [/arch (x86)](../../build/reference/arch-x86.md) et [/arch (x64)](../../build/reference/arch-x64.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/arch:[ARMv7VE|VFPv4]  
```  
  
## <a name="arguments"></a>Arguments  
 **armv7ve**  
 Permet l’utilisation des instructions des extensions de virtualisation ARMv7VE.  
  
 **vfpv4**  
 Permet l'utilisation des instructions ARM VFPv4. Si cette option n'est pas spécifiée, VFPv3 est utilisé par défaut.  
  
## <a name="remarks"></a>Notes  
 Le `_M_ARM_FP` macro (pour ARM uniquement) qui indique, le cas échéant, **/arch** option du compilateur a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).  
  
 Lorsque vous utilisez [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération du code pour les fonctions managées. **/ arch** uniquement affecte génération de code pour les fonctions natives.  
  
### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:ARMv7VE ou /arch:VFPv4 dans Visual Studio  
  
1.  Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Dans le **des options supplémentaires** zone, ajoutez `/arch:ARMv7VE` ou `/arch:VFPv4`.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)