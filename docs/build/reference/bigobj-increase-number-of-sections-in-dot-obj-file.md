---
title: -/bigobj (augmenter nombre de Sections dans. Fichier obj) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bigobj
dev_langs:
- C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df8bc379462bf5937f463b464ea2972472c49808
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369953"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Augmenter le nombre de sections dans le fichier .obj)
**/bigobj** augmente le nombre de sections qu’un fichier objet peut contenir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/bigobj  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, un fichier objet peut contenir jusqu'à 65 536 (2 ^ 16) sections adressables. C’est le cas quel plateforme cible est spécifiée. **/bigobj** augmente cette capacité d’adressage à 4 294 967 296 (2 ^ 32).  
  
 La plupart des modules ne génèrent jamais d’un fichier .obj qui contient plus de 65 536 sections. Toutefois, code généré par ordinateur ou le code qui fait un usage intensif de bibliothèques de modèles peut nécessiter des fichiers .obj pouvant contenir plus de sections. **/bigobj** est activée par défaut sur les projets de plateforme Windows universelle (UWP), car le code XAML généré par l’ordinateur comprend un grand nombre d’en-têtes. Si vous désactivez cette option sur un projet d’application UWP, vous êtes susceptible de rencontrer l’erreur du compilateur C1128.  
  
 Éditeurs de liens fournis avant Visual C++ 2005 ne peut pas lire les fichiers .obj qui ont été générés avec **/bigobj**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)