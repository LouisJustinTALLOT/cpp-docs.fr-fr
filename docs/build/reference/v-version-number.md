---
title: -V (numéro de Version) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3daf62c818b454a5477de04a27c4b4f308c271d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377230"
---
# <a name="v-version-number"></a>/V (Numéro de version)
Obsolète. Incorpore une chaîne de texte dans le fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Chaîne spécifiant le numéro de version ou une mention de copyright à incorporer dans un fichier .obj.  
  
## <a name="remarks"></a>Notes  
 L’étiquette stringcan un fichier .obj avec un numéro de version ou une mention de copyright. Tout caractère espace ou tabulation doit figurer entre guillemets doubles (") si elles font partie de la chaîne. Une barre oblique inverse (\\) doivent précéder les guillemets doubles si elles font partie de la chaîne. Un espace entre **/V** et `string` est facultatif.  
  
 Vous pouvez également utiliser [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md) avec l’argument de type commentaire du compilateur pour placer le nom et numéro de version du compilateur dans le fichier .obj.  
  
 Le **/V** option est déconseillée à compter de Visual Studio 2005 ; **/V** a été principalement utilisée pour prendre en charge la création des pilotes de périphériques virtuels (VxDs), et cette opération n’est plus pris en charge par l’ensemble d’outils Visual C++. Pour obtenir la liste des options du compilateur déconseillées, consultez **déconseillées et supprimées des Options du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).  
  
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