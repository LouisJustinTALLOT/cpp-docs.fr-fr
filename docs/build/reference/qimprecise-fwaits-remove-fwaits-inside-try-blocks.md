---
title: -Qimprecise_fwaits (Supprimer fwaits à l’intérieur des blocs Try) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a688f4b9f8f3c9302bb6a49e4b0a94a0e0931b33
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378052"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Remove fwaits Inside Try Blocks)
Supprime la `fwait` commandes internes `try` bloque lorsque vous utilisez la [/fp : sauf](../../build/reference/fp-specify-floating-point-behavior.md) option du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qimprecise_fwaits  
```  
  
## <a name="remarks"></a>Notes  
 Cette option n’a aucun effet si **/fp : sauf** n’est pas également spécifié. Si vous spécifiez la **/fp : sauf** option, le compilateur insère un `fwait` commande autour de chaque ligne de code dans un `try` bloc. De cette façon, le compilateur peut identifier la ligne de code qui génère une exception spécifique. **/ Qimprecise_fwaits** supprime interne `fwait` obtenir des instructions, en laissant uniquement les attentes autour du `try` bloc. Cela améliore les performances, mais le compilateur pourrez indiquer laquelle `try` bloc lève une exception, et non pas la ligne.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)