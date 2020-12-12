---
description: En savoir plus sur les fichiers d’entrée de lien
title: Fichiers d'entrée LINK
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 3bf25d36ab61b35dfe3d1551e9f85e8c2f26862b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199504"
---
# <a name="link-input-files"></a>Fichiers d'entrée LINK

Vous fournissez à l’éditeur de liens des fichiers contenant des objets, des bibliothèques d’importation et standard, des ressources, des définitions de module et une entrée de commande. LINK n’utilise pas d’extensions de fichier pour faire des hypothèses sur le contenu d’un fichier. Au lieu de cela, LINK examine chaque fichier d’entrée pour déterminer le type de fichier.

Les fichiers objets sur la ligne de commande sont traités dans l’ordre dans lequel ils apparaissent sur la ligne de commande. Les bibliothèques sont également recherchées dans l’ordre des lignes de commande, avec les signes suivants : les symboles qui ne sont pas résolus lors de l’intégration d’un fichier objet à partir d’une bibliothèque sont d’abord recherchés dans cette bibliothèque, puis dans les bibliothèques suivantes à partir de la ligne de commande et de la ligne de commande [/DEFAULTLIB (spécifier la bibliothèque par défaut)](defaultlib-specify-default-library.md)

> [!NOTE]
> Le lien n’accepte plus de point-virgule (ou tout autre caractère) comme début de commentaire dans les fichiers réponse et les fichiers de commande. Les points-virgules sont reconnus uniquement comme le début des commentaires dans les fichiers de définition de module (. def).

LINK utilise les types de fichiers d’entrée suivants :

- [fichiers .obj](dot-obj-files-as-linker-input.md)

- [fichiers. netmodule](netmodule-files-as-linker-input.md)

- [fichiers .lib](dot-lib-files-as-linker-input.md)

- [fichiers. exp](dot-exp-files-as-linker-input.md)

- [fichiers. def](dot-def-files-as-linker-input.md)

- [fichiers. pdb](dot-pdb-files-as-linker-input.md)

- [fichiers. res](dot-res-files-as-linker-input.md)

- [fichiers. exe](dot-exe-files-as-linker-input.md)

- [fichiers .txt](dot-txt-files-as-linker-input.md)

- [fichiers .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
