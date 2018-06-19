---
title: -await (activer la prise en charge des coroutine) | Documents Microsoft
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78a62195ca28be49ed8c00dacacce003281699f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371029"
---
# <a name="await-enable-coroutine-support"></a>/ await (activer la prise en charge des coroutine)  
  
Utilisez le **/ await** option du compilateur pour activer la prise en charge du compilateur pour les coroutines.  
  
## <a name="syntax"></a>Syntaxe  
  
> / await  
  
## <a name="remarks"></a>Notes  
  
Le **/ await** option du compilateur permet la prise en charge du compilateur pour les coroutines C++ et les mots clés **co_await**, **co_yield**, et **co_return**. Cette option est désactivée par défaut. Pour plus d’informations sur la prise en charge pour les coroutines dans Visual Studio, consultez le [Blog de l’équipe Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Pour plus d’informations sur la proposition standard les coroutines, consultez [N4628 projet, les spécifications techniques pour les Extensions C++ pour les Coroutines](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).  

Le **/ await** option est disponible à compter de Visual Studio 2015.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.   
  
2. Sous **propriétés de Configuration**, développez le **C/C++** dossier et choisissez le **ligne de commande** page de propriétés.  
  
3. Entrez le **/ await** option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
  
[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)