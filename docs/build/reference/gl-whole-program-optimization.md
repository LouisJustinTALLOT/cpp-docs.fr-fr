---
title: -GL (optimisation de l’ensemble du programme) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce972b6e7254ad7454f8e8799283588f0fdd5270
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376271"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimisation de l'ensemble du programme)
Active l'optimisation de l'ensemble du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GL[-]  
```  
  
## <a name="remarks"></a>Notes  
 Optimisation de l’ensemble du programme permet au compilateur d’effectuer des optimisations avec des informations sur tous les modules dans le programme. Sans optimisation de l’ensemble du programme, les optimisations sont effectuées sur une base de module (compiland).  
  
 Optimisation de l’ensemble du programme est désactivée par défaut et doit être explicitement activée. Toutefois, il est également possible de désactiver explicitement avec **/GL-**.  
  
 Avec des informations sur tous les modules, le compilateur peut :  
  
-   Optimiser l’utilisation de registres au-delà des limites de fonction.  
  
-   Effectuer un meilleur travail de suivi des modifications apportées aux données globales, autorisant ainsi une réduction du nombre de charges et de magasins.  
  
-   Effectuer un meilleur travail de suivi de l’ensemble possible d’éléments modifiée par un pointeur déréférencé, réduisant ainsi le nombre de charges et de magasins.  
  
-   Incorporer une fonction dans un module, même lorsque la fonction est définie dans un autre module.  
  
 fichiers .obj produits avec **/GL** ne seront pas disponibles sur ces utilitaires de l’éditeur de liens en tant que [EDITBIN](../../build/reference/editbin-reference.md) et [DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
 Si vous compilez votre programme avec **/GL** et [/c](../../build/reference/c-compile-without-linking.md), vous devez utiliser l’option de l’éditeur de liens /LTCG pour créer le fichier de sortie.  
  
 [/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) ne peut pas être utilisé avec **/GL**  
  
 Le format des fichiers produits avec **/GL** dans la version actuelle ne peuvent être lisibles par les versions ultérieures de Visual C++. Vous ne devez pas fournir un fichier .lib composé de fichiers .obj qui ont été générés avec **/GL** , sauf si vous êtes disposé à livrer des copies du fichier .lib pour toutes les versions de Visual C++ que les utilisateurs à utiliser, maintenant et dans le futur.  
  
 fichiers .obj produits avec **/GL** et les fichiers d’en-tête précompilés ne doivent pas servir pour générer un fichier .lib, sauf si le fichier .lib sera lié sur le même ordinateur que celui qui a généré le **/GL** fichier .obj. Pour plus d’informations à partir du fichier d’en-tête précompilé du fichier .obj seront nécessaires au moment de la liaison.  
  
 Pour plus d’informations sur les optimisations disponibles et les limitations de l’optimisation de l’ensemble du programme, consultez [LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/GL** également rend profil optimisation guidée disponibles ; consultez LTCG.  Lors de la compilation pour les optimisations guidées profil si vous souhaitez classer les fonctions de vos optimisations guidées par profil, vous devez compiler avec [/Gy](../../build/reference/gy-enable-function-level-linking.md) ou une option du compilateur qui implique/Gy.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Consultez [/LTCG (génération de Code d’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md) pour plus d’informations sur la façon de spécifier **/GL** dans l’environnement de développement.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)