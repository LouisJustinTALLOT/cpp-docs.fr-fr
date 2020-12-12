---
description: 'En savoir plus sur : choix du format des fichiers d’entrée. netmodule'
title: Choix du format des fichiers d'entrée .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: ed7e448879e983ace7d96cdc7585bf0303378114
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179200"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Choix du format des fichiers d'entrée .netmodule

Un fichier. obj MSIL (compilé avec [/CLR](clr-common-language-runtime-compilation.md)) peut également être utilisé en tant que fichier. netmodule.  les fichiers. obj contiennent des métadonnées et des symboles natifs.  les modules. netmodule contiennent uniquement des métadonnées.

Vous pouvez passer un fichier. obj MSIL à tout autre compilateur Visual Studio à l’aide de l’option du compilateur/addmodule (mais sachez que le fichier. obj devient partie intégrante de l’assembly résultant et doit être fourni avec l’assembly).  Par exemple, Visual C# et Visual Basic disposent de l’option du compilateur/addmodule.

> [!NOTE]
> Dans la plupart des cas, vous devrez passer à l’éditeur de liens le fichier. obj de la compilation qui a créé le module .net.  Le passage d’un fichier de module MSIL. dll ou. netmodule à l’éditeur de liens peut entraîner la LNK1107.

les fichiers. obj, ainsi que leurs fichiers. h associés, que vous référencez via #include dans la source, permettent aux applications C++ d’utiliser les types natifs dans le module, tandis que dans un fichier. netmodule, seuls les types managés peuvent être consommés par une application C++.  Si vous tentez de passer un fichier. obj à #using, les informations sur les types natifs ne seront pas disponibles ; #include à la place le fichier. h du fichier. obj.

Les autres compilateurs Visual Studio peuvent uniquement consommer des types managés à partir d’un module.

Utilisez les éléments suivants pour déterminer si vous devez utiliser un fichier. netmodule ou un fichier. obj comme entrée de module pour l’éditeur de liens MSVC :

- Si vous générez avec un compilateur Visual Studio autre que Visual C++, produisez un. netmodule et utilisez le. netmodule comme entrée de l’éditeur de liens.

- Si vous utilisez le compilateur MSVC pour produire des modules et si le ou les modules seront utilisés pour générer autre chose qu’une bibliothèque, utilisez les fichiers. obj produits par le compilateur comme entrée de module pour l’éditeur de liens ; n’utilisez pas le fichier. netmodule comme entrée.

- Si vos modules sont utilisés pour générer une bibliothèque native (non managée), utilisez des fichiers. obj comme entrée de module dans l’éditeur de liens et générez un fichier de bibliothèque. lib.

- Si vos modules sont utilisés pour générer une bibliothèque managée, et si toutes les entrées de module dans l’éditeur de liens seront vérifiables (générées avec/clr : safe), utilisez les fichiers. obj comme entrée de module pour l’éditeur de liens et générez un fichier de bibliothèque. dll (Assembly) ou. netmodule (module).

- Si vos modules sont utilisés pour générer une bibliothèque managée, et si un ou plusieurs modules sont entrés dans l’éditeur de liens avec juste/CLR, utilisez les fichiers. obj comme entrée de module pour l’éditeur de liens et générez un fichier. dll (Assembly).  Si vous souhaitez exposer des types managés à partir de la bibliothèque et si vous souhaitez également que les applications C++ consomment les types natifs de la bibliothèque, votre bibliothèque se compose des fichiers. obj pour les modules de composant de bibliothèque (vous devez également envoyer les fichiers. h pour chaque module, afin qu’ils puissent être référencés avec #include à partir du code source).

## <a name="see-also"></a>Voir aussi

[Fichiers. netmodule en tant qu’entrée dans l’éditeur de liens](netmodule-files-as-linker-input.md)
