---
title: -WL (activer un diagnostic de ligne) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58a6b41e66f7ec37ad02747edb8331049b9baef5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376785"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (Activer un diagnostic de ligne)
Ajoute des informations supplémentaires à un message d’erreur ou avertissement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/WL  
```  
  
## <a name="remarks"></a>Notes  
 Messages d’erreur et Avertissement du compilateur C++ peuvent être suivis par des informations supplémentaires qui s’affiche, par défaut, sur une nouvelle ligne. Lorsque vous compilez à partir de la ligne de commande, la ligne d’informations supplémentaire peut être ajoutée à l’erreur ou un message d’avertissement. Cela peut être souhaitable si vous capturez votre sortie de génération dans un fichier journal et ensuite traitez ce journal pour rechercher toutes les erreurs et avertissements. Un point-virgule sépare le message d’erreur ou avertissement à partir de la ligne supplémentaire.  
  
 Pas de tous les messages d’erreur et avertissement ont une ligne supplémentaire d’informations. Le code suivant génère une erreur qui possède une ligne supplémentaire d’informations ; Il vous permet de tester l’effet lorsque vous utilisez **/WL**.  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
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