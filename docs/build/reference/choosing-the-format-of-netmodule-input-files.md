---
title: Choix du format des fichiers d'entrée .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320575"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Choix du format des fichiers d'entrée .netmodule

Un fichier MSIL .obj (compilé avec [/clr](clr-common-language-runtime-compilation.md)) peut également être utilisé comme fichier .netmodule.  Les fichiers .obj contiennent des métadonnées et des symboles indigènes.  .netmodules ne contiennent que des métadonnées.

Vous pouvez passer un fichier MSIL .obj à n’importe quel autre compilateur Visual Studio via l’option de compilation /addmodule (mais sachez que le fichier .obj fait partie de l’assemblage résultant et doit être expédié avec l’assemblage).  Par exemple, Visual C et Visual Basic ont l’option de compilateur /addmodule.

> [!NOTE]
> Dans la plupart des cas, vous devrez passer au linker le fichier .obj de la compilation qui a créé le module .net.  Passer un fichier de module MSIL .dll ou .netmodule au linker peut entraîner LNK1107.

.obj fichiers, avec leurs fichiers .h associés, que vous référencez via #include à la source, permettent aux applications C ' de consommer les types natifs dans le module, tandis que dans un fichier .netmodule, seuls les types gérés peuvent être consommés par une application C.  Si vous tentez de transmettre un fichier .obj à #using, des renseignements sur les types autochtones ne seront pas disponibles; #include le fichier .h du fichier .obj à la place.

D’autres compilateurs Visual Studio ne peuvent consommer que des types gérés à partir d’un module.

Utilisez ce qui suit pour déterminer si vous devez utiliser un .netmodule ou un fichier .obj comme entrée de module au linker MSVC :

- Si vous construisez avec un compilateur Visual Studio autre que Visual C, produisez un .netmodule et utilisez le .netmodule comme entrée vers le linker.

- Si vous utilisez le compilateur MSVC pour produire des modules et si le module est utilisé pour construire autre chose qu’une bibliothèque, utilisez les fichiers .obj produits par le compilateur comme entrée du module au linker; n’utilisez pas le fichier .netmodule comme entrée.

- Si vos modules seront utilisés pour construire une bibliothèque native (pas gérée), utilisez des fichiers .obj comme entrée de module au linker et générer un fichier de bibliothèque .lib.

- Si vos modules seront utilisés pour construire une bibliothèque gérée, et si toutes les entrées de module vers le lien seront vérifiables (produites avec /clr:safe), utilisez des fichiers .obj comme entrée de module au linker et générer un fichier de bibliothèque .dll (assemblage) ou .netmodule (module).

- Si vos modules seront utilisés pour construire une bibliothèque gérée, et si un ou plusieurs modules d’entrée au lien seront produits avec juste /clr, utilisez des fichiers .obj comme entrée de module au linker et générer un .dll (assemblage).  Si vous souhaitez exposer les types gérés de la bibliothèque et si vous voulez également que les applications CMD consomment les types natifs dans la bibliothèque, votre bibliothèque se composera des fichiers .obj pour les modules de composants des bibliothèques (vous voudrez également expédier les fichiers .h pour chaque module, afin qu’ils puissent être référencés avec #include à partir du code source).

## <a name="see-also"></a>Voir aussi

[Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](netmodule-files-as-linker-input.md)
