---
title: -Zo (améliorer le débogage optimisé) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 013738ab05bf67d3db066d94d32d398a0555c55e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380273"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (Améliorer le débogage optimisé)
Génère des informations de débogage avancées pour le code optimisé dans des builds autres que debug.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
/Zo[-]  
```  
  
## <a name="remarks"></a>Notes  
 Le **/Zo** commutateur du compilateur génère des informations de débogage avancées pour le code optimisé. L'optimisation peut utiliser des registres pour les variables locales, réorganiser le code, vectoriser les boucles et placer les appels de fonction inline. Ces optimisations peuvent rendre moins visible la relation entre le code source et le code objet compilé. Le **/Zo** commutateur indique au compilateur de générer des informations de débogage supplémentaires pour les variables locales et des fonctions inline. Il permet de voir les variables dans le **automatique**, **variables locales**, et **espion** windows lorsque vous parcourez le code dans le débogueur Visual Studio optimisé. Il permet également aux traces de pile d'afficher les fonctions inline dans le débogueur WinDBG. Déboguer les builds qui les optimisations sont désactivées ([/Od](../../build/reference/od-disable-debug.md)) n’avez pas besoin d’informations de débogage supplémentaires générées quand **/Zo** est spécifié. Utilisez le **/Zo** commutateur pour déboguer des configurations Release avec l’optimisation activée. Pour plus d’informations sur les commutateurs d’optimisation, consultez [/O (optimiser le Code), Options](../../build/reference/o-options-optimize-code.md). Le **/Zo** est activée par défaut dans Visual Studio lorsque vous spécifiez des informations de débogage avec **/Zi** ou **/Z7**. Spécifiez **/Zo-** désactiver explicitement cette option du compilateur.  
  
 Le **/Zo** commutateur est disponible à partir de Visual Studio 2013 Update 3, et il remplace le précédemment non documenté **/d2Zi+** basculer.  
  
### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /Zo dans Visual Studio  
  
1.  Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Modifier la **des Options supplémentaires** propriété à inclure `/Zo` , puis **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)   
 [/ Z7, / Zi, /ZI (Format des informations de débogage)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [Modifier & Continuer](/visualstudio/debugger/edit-and-continue)