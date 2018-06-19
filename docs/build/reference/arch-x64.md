---
title: -arch (x64) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 848d229d6cf8df7d08494d0c300e082c6dc7d0a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371669"
---
# <a name="arch-x64"></a>/arch (x64)
Spécifie l'architecture pour la génération de code sur x64. Consultez également [/arch (x86)](../../build/reference/arch-x86.md) et [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/arch:[AVX|AVX2]  
```  
  
## <a name="arguments"></a>Arguments  
 **/ arch : AVX**  
 Active l’utilisation des instructions Intel Advanced Vector Extensions.  
  
 **/ arch : avx2**  
 Active l’utilisation des instructions Intel Advanced Vector Extensions 2.  
  
## <a name="remarks"></a>Notes  
 **/ arch** uniquement affecte génération de code pour les fonctions natives. Lorsque vous utilisez [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération du code pour les fonctions managées.  
  
 Le `__AVX__` symbole de préprocesseur est défini lorsque la **/arch : AVX** option du compilateur est spécifiée. Le `__AVX2__` symbole de préprocesseur est défini lorsque la **/arch : avx2** option du compilateur est spécifiée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md). Le **/arch : avx2** option a été introduite dans Visual Studio 2013 Update 2, version 12.0.34567.1.  
  
### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:AVX ou /arch:AVX2 dans Visual Studio  
  
1.  Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.  
  
3.  Sélectionnez le **génération de Code** page de propriétés.  
  
4.  Dans le **activation du jeu d’instructions amélioré** liste déroulante, choisissez **Advanced Vector Extensions (/ arch : AVX)** ou **Advanced Vector Extensions 2 (/ arch : AVX2)**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)