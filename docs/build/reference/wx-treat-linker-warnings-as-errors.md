---
title: -WX (traiter les avertissements de l’éditeur de liens comme des erreurs) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /WX
dev_langs:
- C++
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 686b17a3db00175340e3490241c6c2e9f9325225
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377285"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Traiter les avertissements de l'Éditeur de liens comme des erreurs)
```  
/WX[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 /WX ne provoque aucun fichier de sortie est généré si l’éditeur de liens génère un avertissement.  
  
 Cela revient à **/WX** pour le compilateur (voir [Wn, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, Wall, /wd, / nous, /wo, /WV., /Won (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) pour plus d’informations). Toutefois, la spécification **/WX** pour la compilation n’implique pas que **/WX** sera également en vigueur pour la phase de liaison ; vous devez spécifier explicitement **/WX** pour chaque outil.  
  
 Par défaut, **/WX** n’est pas en vigueur. Pour traiter les avertissements de l’éditeur de liens comme des erreurs, spécifiez **/WX**. **/WX:no** équivaut à ne pas spécifier **/WX**.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l’option dans le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)