---
title: -Oi (générer des fonctions intrinsèques) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f28051f5d7aaaa4606fffa4d4c94fb2086031419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375839"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Générer des fonctions intrinsèques)
Remplace certains appels de fonction avec des formes intrinsèques ou sinon spéciaux de la fonction permettant à votre application s’exécute plus rapidement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Oi[-]  
```  
  
## <a name="remarks"></a>Notes  
 Les programmes qui utilisent des fonctions intrinsèques sont plus rapides, car ils n’ont pas la surcharge d’appels de fonction, mais peuvent être plus volumineux en raison du code supplémentaire créé.  
  
 Consultez [intrinsèque](../../preprocessor/intrinsic.md) pour plus d’informations sur les fonctions possédant des formes intrinsèques.  
  
 **/Oi** est uniquement une demande au compilateur de remplacer des appels de fonctions intrinsèques ; le compilateur peut appeler la fonction (et pas remplacer l’appel de fonction intrinsèque) si cela entraîne de meilleures performances.  
  
 **x86 spécifiques**  
  
 Les fonctions à virgule flottante intrinsèques ne pas effectuer les vérifications spéciales sur les valeurs d’entrée ainsi travailler dans des plages restreints d’entrée et ont différentes exceptions et les restrictions que les routines de bibliothèque portant le même nom. À l’aide de formes intrinsèques véritables implique la perte de gestion des exceptions IEEE, ainsi la perte de `_matherr` et `errno` fonctionnalité ; cette dernière implique la perte de compatibilité ANSI. Toutefois, les formes intrinsèques peuvent accélérer considérablement floating-point-nécessitant beaucoup de programmes, et pour de nombreux programmes, les problèmes de conformité sont peu d’intérêt pratique.  
  
 Vous pouvez utiliser la [Za](../../build/reference/za-ze-disable-language-extensions.md) option du compilateur pour substituer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.  
  
 **FIN x86 spécifique**  
  
 Vous utilisez également [intrinsèque](../../preprocessor/intrinsic.md) pour créer des fonctions intrinsèques ou [(fonction) (C/C++)](../../preprocessor/function-c-cpp.md) pour forcer explicitement un appel de fonction.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **optimisation** page de propriétés.  
  
4.  Modifier la **activation des fonctions intrinsèques** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [compilateur, fonctions intrinsèques](../../intrinsics/compiler-intrinsics.md)