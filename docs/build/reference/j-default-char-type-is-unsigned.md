---
title: -J (caractère par défaut est de Type non signé) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93172296b0e2e6d54dc428ffc62812ad979b160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374464"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Type de caractère par défaut non signé)
Modifie la valeur par défaut `char` type à partir de `signed char` à `unsigned char`et le `char` type est étendu par zéro lorsqu’elle est élargie à un `int` type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/J  
```  
  
## <a name="remarks"></a>Notes  
 Si un `char` valeur est déclarée explicitement comme `signed`, le **/J** option n’affecte pas, et la valeur est étendue avec un signe lorsqu’elle est élargie à un `int` type.  
  
 Le **/J** option définit `_CHAR_UNSIGNED`, qui est utilisé avec `#ifndef` dans le fichier LIMITS.h pour définir la plage de la valeur par défaut `char` type.  
  
 ANSI C et C++ ne nécessitent pas une implémentation spécifique de la `char` type. Cette option est utile lorsque vous travaillez avec des données de caractères qui seront finalement converties dans une langue autre que l’anglais.  
  
> [!NOTE]
>  Si vous utilisez cette option du compilateur avec ATL/MFC, une erreur peut être générée. Bien que vous pouvez désactiver cette erreur en définissant `_ATL_ALLOW_CHAR_UNSIGNED`, cette solution de contournement n’est pas prise en charge et peut ne pas toujours fonctionner.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans le projet **Pages de propriétés** boîte de dialogue, dans le volet gauche sous **propriétés de Configuration**, développez **C/C++** , puis sélectionnez **la ligne de commande**.  
  
3.  Dans le **des Options supplémentaires** volet, spécifiez la **/J** option du compilateur.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md)