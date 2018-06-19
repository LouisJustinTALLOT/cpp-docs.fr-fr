---
title: Choix du Format de fichier .netmodule des fichiers d’entrée | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62575d3e816bdc10587e7a4c9cebcea735329ec1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372719"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Choix du format des fichiers d'entrée .netmodule
Un fichier .obj MSIL (compilé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)) peut également être utilisé comme un fichier .netmodule.  les fichiers .obj contiennent des métadonnées et des symboles natifs.  fichiers .netmodule contiennent uniquement des métadonnées.  
  
 Vous pouvez passer un fichier .obj MSIL pour les autres compilateurs Visual Studio via l’option du compilateur /addmodule (mais n’oubliez pas que le fichier .obj devient partie intégrante de l’assembly résultant et doit être fourni avec l’assembly).  Par exemple, Visual c# et Visual Basic ont l’option du compilateur /addmodule.  
  
> [!NOTE]
>  Dans la plupart des cas, vous devez passer à l’éditeur de liens le fichier .obj de la compilation qui a créé le module .net.  Passage d’un fichier de module MSIL .dll ou .netmodule à l’éditeur de liens peut entraîner l’erreur LNK1107.  
  
 les fichiers .obj, ainsi que leurs fichiers .h associés que vous pouvez référencer via #include dans la source, d’autoriser les applications C++ utilisent les types natifs dans le module, tandis que dans un fichier .netmodule, seuls les types managés peuvent être utilisés par une application C++.  Si vous tentez de passer un fichier .obj à #using, plus d’informations sur les types natifs pas seront disponibles. #include le fichier .h du fichier .obj à la place.  
  
 Autres compilateurs Visual Studio peuvent uniquement utiliser des types managés à partir d’un module.  
  
 Pour déterminer si vous devez utiliser un fichier .netmodule ou un fichier .obj comme entrée de module dans l’éditeur de liens Visual C++, utilisez les éléments suivants :  
  
-   Si vous générez avec un compilateur Visual Studio autre que Visual C++, produisez un fichier .netmodule et utilisez-le comme entrée dans l’éditeur de liens.  
  
-   Si vous utilisez le compilateur Visual C++ pour produire des modules et si l’ou les modules doivent être utilisé pour créer autre chose qu’une bibliothèque, utilisez les fichiers .obj produits par le compilateur comme entrée de module dans l’éditeur de liens ; n’utilisez pas le fichier .netmodule en tant qu’entrée.  
  
-   Si vos modules sont utilisés pour générer une bibliothèque native (non managée), utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générer un fichier de bibliothèque .lib.  
  
-   Si vos modules sont utilisés pour générer une bibliothèque managée et si toutes les entrées de module dans l’éditeur de liens sont vérifiables (produites avec/clr : safe), utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générer un fichier .dll (assembly) ou un fichier de bibliothèque .netmodule (module).  
  
-   Si vos modules sont utilisés pour générer une bibliothèque managée, et si une ou plusieurs entrées de modules pour l’éditeur de liens sont produites avec /clr uniquement, utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générez un fichier .dll (assembly).  Si vous souhaitez exposer des types managés à partir de la bibliothèque et si vous souhaitez également les applications C++ utilisent les types natifs dans la bibliothèque, votre bibliothèque se compose des fichiers .obj pour les modules de composant de bibliothèques (vous souhaiterez également expédier les fichiers .h pour chaque module. afin qu’ils peuvent être référencées avec #include à partir de code source).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)