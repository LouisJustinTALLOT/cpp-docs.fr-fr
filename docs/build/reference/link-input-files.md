---
title: Fichiers d'entrée LINK
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817788"
---
# <a name="link-input-files"></a>Fichiers d'entrée LINK

Vous fournissez l’éditeur de liens avec les fichiers qui contiennent des objets, des bibliothèques standards, ressources, les définitions de module et d’importation d’entrée de commande. LIEN n’utilise pas les extensions de fichier pour faire des hypothèses sur le contenu d’un fichier. Au lieu de cela, le lien examine chaque fichier d’entrée pour déterminer quel type de fichier, il s’agit.

Fichiers d’objet sur la ligne de commande sont traités dans l’ordre de qu'apparition sur la ligne de commande. Bibliothèques sont recherchés dans l’ordre de ligne de commande, avec la restriction suivante : Les symboles non résolus lorsque mise dans un fichier de l’objet à partir d’une bibliothèque sont recherchés dans cette bibliothèque tout d’abord, puis sur les bibliothèques suivantes à partir de la ligne de commande et [/DEFAULTLIB (spécifier la bibliothèque par défaut)](defaultlib-specify-default-library.md) directives, puis pour toutes les bibliothèques au début de la ligne de commande.

> [!NOTE]
>  LIEN n’accepte plus de point-virgule (ou tout autre caractère) comme le début d’un commentaire dans les fichiers de réponse et les fichiers de commande. Des points-virgules sont reconnus uniquement au début des commentaires dans les fichiers de définition de module (.def).

LIEN utilise les types de fichiers d’entrée suivants :

- [fichiers .obj](dot-obj-files-as-linker-input.md)

- [fichiers .netmodule](netmodule-files-as-linker-input.md)

- [fichiers .lib](dot-lib-files-as-linker-input.md)

- [fichiers .exp](dot-exp-files-as-linker-input.md)

- [fichiers .def](dot-def-files-as-linker-input.md)

- [.pdb files](dot-pdb-files-as-linker-input.md)

- [fichiers .res](dot-res-files-as-linker-input.md)

- [fichiers .exe](dot-exe-files-as-linker-input.md)

- [fichiers .txt](dot-txt-files-as-linker-input.md)

- [fichiers .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
