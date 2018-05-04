---
title: -Fm (nom de fichier de mappage) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fm
dev_langs:
- C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a499b943fcd3213aa76876c65c3aac2dd79060
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="fm-name-mapfile"></a>/Fm (Nom de fichier de mappage)
Indique à l’éditeur de liens pour générer un fichier de mappage contenant une liste des segments dans l’ordre dans lequel ils apparaissent dans le fichier .exe correspondant ou la DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, le fichier de mappage reçoit le nom de base du fichier source C ou C++ correspondant avec une. Extension de carte.  
  
 Spécification de **/Fm** a le même effet que si vous aviez spécifié la [/MAP (générer fichier de mappage)](../../build/reference/map-generate-mapfile.md) option de l’éditeur de liens.  
  
 Si vous spécifiez [/c (compiler sans liaison)](../../build/reference/c-compile-without-linking.md) pour supprimer la liaison, **/Fm** n’a aucun effet.  
  
 Symboles globaux dans un fichier de mappage ont généralement un ou plusieurs au début des traits de soulignement, car le compilateur ajoute un trait de soulignement pour les noms de variables. De nombreux symboles globaux qui s’affichent dans le fichier de mappage sont utilisés en interne par le compilateur et les bibliothèques standards.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)