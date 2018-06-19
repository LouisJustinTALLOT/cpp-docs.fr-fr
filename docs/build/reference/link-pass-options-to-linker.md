---
title: -link (Options de passage à l’éditeur de liens) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b22e21022162a0f9f75e41e3e0bfdce348947e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373291"
---
# <a name="link-pass-options-to-linker"></a>/link (Passer des options à l'Éditeur de liens)
Passe une ou plusieurs options de l’éditeur de liens à l’éditeur de liens.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>Arguments  
 `linkeroptions`  
 Les options à passer à l’éditeur de liens ou l’option de l’éditeur de liens.  
  
## <a name="remarks"></a>Notes  
 Le **/link** option et ses options de l’éditeur de liens doivent apparaître après les noms de fichiers et les options CL. Un espace est requis entre **/link** et `linkeroptions`. Pour plus d’informations, consultez [définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur une page de propriétés de l’éditeur de liens.  
  
4.  Modifier une ou plusieurs propriétés.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Cette option du compilateur ne peut pas être modifiée par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)