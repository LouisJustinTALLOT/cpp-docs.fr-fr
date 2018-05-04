---
title: -maintenant la touche - vmb, /vmg (méthode de représentation) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vmb
- /vmg
dev_langs:
- C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5263b6c7ca227a10b34c32e0b0801eeddf07b9cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (Méthode de représentation)
Sélectionnez la méthode que le compilateur utilise pour représenter les pointeurs vers des membres de classe.  
  
 Utilisez **/vmb** si vous définissez toujours une classe avant de déclarer un pointeur vers un membre de la classe.  
  
 Utilisez **/vmg** pour déclarer un pointeur vers un membre d’une classe avant de définir la classe. Cette situation peut se présenter si vous définissez des membres dans deux classes différentes qui font référence à l’autre. Pour de telles classes mutuellement référence, une classe doit être référencée avant d’être définie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/vmb  
/vmg  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez également utiliser [pointers_to_members](../../preprocessor/pointers-to-members.md) ou [mots clés d’héritage](../../cpp/inheritance-keywords.md) dans votre code pour spécifier une représentation de pointeur.  
  
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