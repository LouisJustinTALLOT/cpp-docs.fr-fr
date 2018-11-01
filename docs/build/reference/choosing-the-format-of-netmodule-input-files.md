---
title: Choix du format des fichiers d'entrée .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: 92f7aafa102a8591192f4394aee62afe86bb3549
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444315"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Choix du format des fichiers d'entrée .netmodule

Un fichier .obj MSIL (compilé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)) peut également être utilisé comme un fichier .netmodule.  les fichiers .obj contiennent des métadonnées et des symboles natifs.  fichiers .netmodule contiennent uniquement des métadonnées.

Vous pouvez passer d’un fichier .obj MSIL à tout autre compilateur Visual Studio via l’option de compilateur /addmodule (mais n’oubliez pas que le fichier .obj devient partie intégrante de l’assembly résultant et doit être livré avec l’assembly).  Par exemple, Visual c# et Visual Basic ont l’option de compilateur /addmodule.

> [!NOTE]
>  Dans la plupart des cas, vous devrez passer à l’éditeur de liens le fichier .obj de la compilation qui a créé le module .net.  Passage d’un fichier de module MSIL .dll ou .netmodule à l’éditeur de liens peut entraîner l’erreur LNK1107.

fichiers .obj, ainsi que leurs fichiers .h associés, qui vous font référence via #include dans source, autoriser les applications C++ utilisent les types natifs dans le module, tandis que dans un fichier .netmodule, seuls les types managés peuvent être utilisés par une application C++.  Si vous essayez de transmettre un fichier .obj à #using, plus d’informations sur les types natifs sera pas disponibles ; #include le fichier .h du fichier .obj à la place.

Autres compilateurs Visual Studio peuvent uniquement consommer des types managés à partir d’un module.

Utilisez les éléments suivants pour déterminer s’il faut utiliser un fichier .netmodule ou un fichier .obj comme entrée de module dans l’éditeur de liens Visual C++ :

- Si vous générez avec un compilateur de Visual Studio que Visual C++, produisez un fichier .netmodule et utilisez-le comme entrée dans l’éditeur de liens.

- Si vous utilisez le compilateur Visual C++ pour produire des modules et si l’ou les modules doivent être utilisé pour générer autre chose qu’une bibliothèque, utilisez les fichiers .obj produits par le compilateur comme entrée de module dans l’éditeur de liens ; n’utilisez pas le fichier .netmodule en tant qu’entrée.

- Si vos modules sont utilisés pour générer une bibliothèque native (et non managée), utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générer un fichier de bibliothèque .lib.

- Si vos modules doivent être utilisés pour générer une bibliothèque managée, et si toutes les entrées de module dans l’éditeur de liens sont vérifiables (produites avec/clr : safe), utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générer un fichier .dll (assembly) ou un fichier de bibliothèque .netmodule (module).

- Si vos modules doivent être utilisés pour générer une bibliothèque managée, et si une ou plusieurs entrées de modules à l’éditeur de liens sont produites avec/CLR uniquement, utilisez les fichiers .obj en tant qu’entrée de module dans l’éditeur de liens et générer un fichier .dll (assembly).  Si vous souhaitez exposer des types managés à partir de la bibliothèque et si vous souhaitez également des applications C++ utilisent les types natifs dans la bibliothèque, votre bibliothèque se compose des fichiers .obj pour les modules de composant de bibliothèques (vous souhaiterez également expédier les fichiers .h de chaque module afin qu’ils peuvent être référencés avec #include à partir de code source).

## <a name="see-also"></a>Voir aussi

[Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)